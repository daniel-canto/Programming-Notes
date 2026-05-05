#backend/java/frameworks_java/java_spring/tecnicas_java_spring 
#jakarta 

```table-of-contents
```

### Visão geral
Essa annotation é fornecida pelo Jakarta, onde somos capazes de realizar validações em campos da body ou query param de forma simples e abstraída.
O [[Annotations Spring#@Valid|@Valid]] vai justamente onde nós queremos realizar nossa validação: por exemplo, ela se encaixa dentro do Controller, bem no argumento onde passamos o nosso DTO de request.
Exemplo: 
```java
public ResponseEntity<InviteCreateResponse> createInvite(@RequestBody @Valid InviteCreateRequest inviteCreateRequest, Authentication authentication)
```
Dessa forma, todas as validações são feitas e além disso, suas exceções podem ser tratadas, que veremos a seguir.

Abaixo, estão algumas das principais annotations usadas para validação de campos com o Jakarta:

Vale ressaltar, que todas as annotations possuem o parâmetro `message`, que nos permite lançar uma mensagem customizada ao cliente, por exemplo:
`String message, @NotNull(message="Campo 'nome' obrigatório.")`. 

##### @NotNull
Valida campos que não podem ser nulos e são obrigatórios. 
##### @Email
Valida se um campo é um email válido.

---
### Como tratar sua exceção
Para tratar a exceção do @Valid do Jakarta, podemos utilizar o [[Annotations Spring#@RestControllerAdvice|@RestControllerAdvice]], que é uma das forma mais comuns de tratar exceções, vista na anotação [[Tratamento de exceções em Java Spring#Como tratar exceções que já são tratadas pelo Spring?|Como tratar exceções que já são tratadas pelo Spring?]].

Supondo que você já tenha uma classe "RestExceptionHandler" ou algo similar, que contenha a @RestControllerAdvice, você deve estender a classe `ResponseEntityExceptionHandler` e depois, sobrescrever o método responsável por lançar a exceção `MethodArgumentNotValidException`, dessa forma:

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
``` 
Dessa forma, você consegue sobrescrever o tratamento da exceção e customizar ela. 