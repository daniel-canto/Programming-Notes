#backend/java/tecnicas_java/conversao_de_tipos 

```table-of-contents
```

Em Java, por ser uma linguagem fortemente tipada, há alguns cenários de conversão que utilizam sintaxes específicas, que serão listadas abaixo.

### Double para Inteiro
Aqui utilizamos o cast.
Para fazer uma conversão simples, use o exemplo abaixo:
```java
double resultado = 1.4;
int resultadoInt = (int) resultado;

// OU

int resultadoInt = resultado;
```

----
### Inteiro para Double 
Aqui utilizamos o cast.
Para fazer uma conversão simples, use o exemplo abaixo:
```java
int resultado = 5;
double resultadoInt = (int) resultado;

// OU

double resultadoInt = resultado;
```

---
### String para Inteiro
Aqui precisamos usar o parse.
Para fazer uma conversão simples, use o exemplo abaixo:
```java
String meuString = "10";
int meuInt = Integer.parseInt(meuString);
```

---
### Inteiro para Stirng
Aqui precisamos usar o parse.
Para fazer uma conversão simples, use o exemplo abaixo:
```java
int meuInt = 10;
String meuString = String.valueOf(meuInt);
```
