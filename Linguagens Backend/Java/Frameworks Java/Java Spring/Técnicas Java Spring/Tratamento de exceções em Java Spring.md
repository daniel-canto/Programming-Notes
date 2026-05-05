#backend/java/frameworks_java/java_spring/tecnicas_java_spring/tratamento_de_excecoes_em_java_spring

```table-of-contents
```

Essa anotação demonstra como podemos tratar as exceções das nossas aplicações no [[Java Spring]].

### Como tratar as exceções
Para tratar as exceções, é muito simples, portanto, vou detalhar alguns grandes passos principais abaixo.

#### 1. Criando o handler global com [[Annotations Spring#@RestControllerAdvice|@RestControllerAdvice]] 
Primeiro, precisamos criar o handler global que irá mapear todas as exceções que podem lançadas na aplicação e tratar elas. Portanto, para isso criamos um novo pacote (pode ser configs ou infra) e logo em seguida, criamos uma nova classe com um nome objetivo, como `RestExceptionHandler`.

Após criar a classe, precisamos colocar a annotation @RestContollerAdvice em cima da classe e também estender ela com `ResponseEntityExceptionHandler`, dessa forma:
```java title: "RestExceptionHandler"
@RestControllerAdvice  
public class RestExceptionHandler extends ResponseEntityExceptionHandler {  
  
}
```

#### 2. Criando um DTO para retornar mensagem de erro padronizada
Agora, podemos criar um DTO para ser a nossa response padrão quando um erro for lançado. Portanto, criamos a seguinte DTO:
```java
import org.springframework.http.HttpStatus;  
  
import java.time.Instant;  
  
public record ErrorResponse (int status, HttpStatus statusMessage, String errorMessage, Instant timestamp) {  
    public ErrorResponse(int status, HttpStatus statusMessage, String errorMessage) {  
        this(status, statusMessage, errorMessage, Instant.now());  
    }  
}
```
Com isso, temos agora uma estrutura definida para retornar nossas exceções ao cliente.

#### 3. Criando super exceção customizada
Agora, podemos criar nossas exceções customizadas. Para isso, uma grande recomendação é antes, criarmos a nossa Super Exceção Customizada, pois é ela que vai passar sua herança para as demais exceções. Portanto, se algo for alterado, como a adição de um novo atributo, todas as exceções herdam essa característica.
Para isso, criamos uma classe chamada `BusinessException` que estende uma exceção padrão do Java, como a `RuntimeException`, dessa forma:
```java
package com.cofrinho.exceptions;  
  
public class BusinessException extends RuntimeException {  
    public BusinessException(String message) {  
        super(message);  
    }  
}
```

Criamos um construtor que recebe a mensagem para instanciarmos a Super Classe `RuntimeException` e assim podemos armazenar a mensagem de exceção corretamente, pois essa mensagem é passada para cada superclasse até chegar na Throwable do Java, dessa forma:
```java
Throwable → armazena a mensagem em detailMessage Exception RuntimeException BusinessException → super(message) propaga até Throwable
```

#### 4. Criando as exceptions customizadas
Agora, vamos criar as exceptions customizadas. Aqui, eu particularmente não gosto de criar exceptions para cada entidade, como por exemplo UserNotFound, ProdutctNotFound e assim por diante. 

Eu prefiro deixar elas genéricas e dinâmicas, por exemplo, ResourceNotFound, passando uma mensagem customizada e mantendo o status http code padrão, nesse caso 404.

Agora, vamos criar uma das exceções de exemplo, para isso, criamos uma nova classe, como a `ResourceNotFoundException`, dessa forma;
```java
public class ResourceNotFoundException extends BusinessException {  
    public ResourceNotFoundException(String message) {  
        super(message);  
    }  
}
```
Como podemos ver, criamos uma exceção que herda características do `BusinessException `criado antes, criamos um construtor que recebe a mensagem e passamos essa mensagem para a super classe.

Dessa forma, a nossa exceção customizada está pronta. Podemos agora mapear cada uma delas.

##### 5. Mapeamento de exceções
Agora, vamos criar um handler para cada exceção, portanto, vamos na nossa `ResponseEntityExceptionHandler` e mapeamentos nossos handlers e exceções com a annotation [[Annotations Spring#@ExceptionHandler|@ExceptionHandler]], dessa forma:
```java
@ExceptionHandler(ResourceNotFoundException.class)  
public ResponseEntity<ErrorResponse> handleNotFound(ResourceNotFoundException e) {  
    return ResponseEntity.status(HttpStatus.NOT_FOUND)  
            .body(new ErrorResponse(HttpStatus.NOT_FOUND.value(), HttpStatus.NOT_FOUND, e.getMessage()));  
}
```
Note que quando a exceção é capturada, uma lógica de criar um novo DTO utilizando a mensagem da exceção é realizada, dessa forma, garantimos o retorno tratado das exceções do nosso sistema.

----
### Como tratar todas as exeções possíveis inesperadas?
**É importante ressaltar que o @RestControllerAdvice para tratamento de mapeia a exceção para a exceção mais específica**.
I~={green}sso é, se temos uma exceção que é herda diretamente a `BusinessException`, a exceção mapeada será ela, por ser a mais específica, sendo a mais aproximada da exceção real.
=~
Por exemplo, é impossível nós realizarmos o mapeamento um a um para todas as exceções nativas do Java que podem ocorrer com bugs inesperados, como o NullPointerException por exemplo, que pode ocorrer a qualquer hora.

Portanto, a dica aqui é: para tratar erros completamente inesperados do Java, devemos mapear as classes mais gerais por segurança, como a `BusinessException` e até mesmo a classe suprema de exceção do Java, a própria `Exception`.

Para isso, podemos fazer da seguinte forma:
```java
// Tratando a exceção suprema do Java (trata todos os erros inesperados)
@ExceptionHandler(Exception.class)  
public ResponseEntity<ErrorResponse> handleException(Exception e) {  
    return ResponseEntity.status(HttpStatus.INTERNAL_SERVER_ERROR)  
            .body(new ErrorResponse(HttpStatus.INTERNAL_SERVER_ERROR.value(), HttpStatus.INTERNAL_SERVER_ERROR,  
                    "Houve um erro de processamento."));  
}

// Tratando a exceção pai das nossas exceções customizadas. Se uma delas não for mapeada, ainda será tratada.
@ExceptionHandler(BusinessException.class)  
public ResponseEntity<ErrorResponse> handleBusinessException(BusinessException e) {  
    return ResponseEntity.status(HttpStatus.BAD_REQUEST)  
            .body(new ErrorResponse(HttpStatus.BAD_REQUEST.value(), HttpStatus.BAD_REQUEST,  
                    "Houve um erro de processamento."));  
}
```

Assim, garantimos que todas as exceções inesperadas também sejam devidamente tratadas para o cliente.

---
### Como tratar exceções que já são tratadas pelo Spring?
Algumas exceções já são tratadas pelo Spring, como é o caso que acontece na [[Validação de campos com @Valid#Como tratar sua exceção|Como tratar exceção do @Valid]], onde o próprio Spring já trata essa exceção. 

 Se nós quisermos customizar esse retorno (o que é muito interessante), podemos simplesmente sobrescrever alguns métodos da super classe que herdamos (`ResponseEntityExceptionHandler`).
 
 Abaixo, tem algumas das principais exceções do spring já customizadamente tratadas, só ajustar conforme suas necessidades de retorno.
 ```java
// Override to handle Jakarta exceptions (@Valid)  
@Override  
protected ResponseEntity<Object> handleMethodArgumentNotValid(  
        MethodArgumentNotValidException ex,  
        HttpHeaders headers,  
        HttpStatusCode status,  
        WebRequest request) {  
  
    String errors = ex.getBindingResult()  
            .getFieldErrors()  
            .stream()  
            .map(f -> f.getDefaultMessage())  
            .collect(Collectors.joining(", "));  
  
    return ResponseEntity.status(HttpStatus.BAD_REQUEST)  
            .body(new ErrorResponse(400, HttpStatus.BAD_REQUEST, errors));  
}  
  
// Override to handle invalid requests  
@Override  
protected ResponseEntity<Object> handleHttpMessageNotReadable(  
        HttpMessageNotReadableException e,  
        HttpHeaders headers,  
        HttpStatusCode status,  
        WebRequest request) {  
  
    return ResponseEntity.status(HttpStatus.BAD_REQUEST)  
            .body(new ErrorResponse(400, HttpStatus.BAD_REQUEST, "Requisição inválida ou mal formatada."));  
}  
  
@Override  
protected ResponseEntity<Object> handleHttpMediaTypeNotSupported(  
        HttpMediaTypeNotSupportedException ex,  
        HttpHeaders headers,  
        HttpStatusCode status,  
        WebRequest request) {  
  
    return ResponseEntity.status(HttpStatus.UNSUPPORTED_MEDIA_TYPE)  
            .body(new ErrorResponse(415, HttpStatus.UNSUPPORTED_MEDIA_TYPE, "Formato de mídia não suportado."));  
}  
  
@Override  
protected ResponseEntity<Object> handleHttpRequestMethodNotSupported(  
        HttpRequestMethodNotSupportedException e,  
        HttpHeaders headers,  
        HttpStatusCode status,  
        WebRequest request) {  
  
    return ResponseEntity.status(HttpStatus.METHOD_NOT_ALLOWED)  
            .body(new ErrorResponse(405, HttpStatus.METHOD_NOT_ALLOWED, "Método HTTP não suportado."));  
}  
  
@Override  
protected ResponseEntity<Object> handleNoResourceFoundException(  
        NoResourceFoundException e,  
        HttpHeaders headers,  
        HttpStatusCode status,  
        WebRequest request) {  
  
    return ResponseEntity.status(HttpStatus.UNSUPPORTED_MEDIA_TYPE)  
            .body(new ErrorResponse(415, HttpStatus.UNSUPPORTED_MEDIA_TYPE, "Formato de mídia não suportado."));  
}
 ```