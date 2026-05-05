#backend/java/conceitos_e_recursos/record

```table-of-contents
```

### O que é?
Os Records foram introduzidos no Java 16 e são uma forma moderna e concisa de criar classes cujo objetivo principal é apenas transportar dados.

Eles funcionam como "Classes de dados" imutáveis que eliminam quase todo o código repetitivo (boilerplate) que costumávamos escrever.

### Objetivo e Utilização
Antes, quando queríamos criar uma classe simples para representar um cliente por exemplo, apenas com nome e email, precisávamos escrever muito código, pois precisávamos definir os getters, o construtor e o toString, como demonstra o código abaixo:
```java
// POJO Tradicional
public class Cliente {
    private final String nome;
    private final String email;

    // 1. Construtor
    public Cliente(String nome, String email) {
        this.nome = nome;
        this.email = email;
    }

    // 2. Getters
    public String getNome() { return nome; }
    public String getEmail() { return email; }

    // 3. equals() e hashCode() (para comparar objetos e usar em Maps/Sets)
    @Override
    public boolean equals(Object o) { ... }
    @Override
    public int hashCode() { ... }

    // 4. toString() (para imprimir bonito no log)
    @Override
    public String toString() { ... }
}
```

Portanto, para solucionar isso, foi criado o Records, que assumem que você deseja apenas guardar dados, portanto, ele gera isso tudo para você automaticamente:
```java
public record Cliente(String nome, String email) { }
```
Apenas essa linha é o suficiente, o compilador Java gera automaticamente o construtor público com os argumentos, os campos privados e finais (imutáveis), os métodos de acesso (podendo ser utilizados dessa forma: `cliente.nome()`, assim seria retornado o nome desse cliente) e as implementações de `equals()`, `hashCode()` e `toString()`.

