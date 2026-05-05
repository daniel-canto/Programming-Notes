#backend/java/conceitos_e_recursos/stream_api 

```table-of-contents
```

### O que é?
A Stream API foi introduzida no Java 8, ela mudou a forma como programamos em Java. Ela permite processar [[Java Collection|collections]] de objetos (como o List, Set, Map) de maneira declarativa e funcional.
A Stream API funciona como uma linha de montagem industrial. A coleção (Lista) é o tanque de matérias-primas. O `Stream` (fluxo) é a esteira rolante que passa por essas matérias por várias estações de trabalho (filtros, transformadores) até chegar no produto final.

----
### Diferença entre Imperativo e Declarativo
Antes da Stream API, usávamos o estilo **Imperativo** (focamos no "Como fazer" usando `for`, `if` e variáveis temporárias). Com a Stream API, usamos o estilo **Declarativo** (focamos no "O que eu quero").

##### Cenário
Vamos supor que temos uma lista de nomes e queremos filtrar apenas os que começam com "A", transformá-los em letras maiúsculas e ordenar.

###### Jeito antigo (Imperativo)
```java
List<String> nomes = Arrays.asList("Ana", "Pedro", "Amanda", "Bruno");
List<String> resultado = new ArrayList<>();

for (String nome : nomes) {
    if (nome.startsWith("A")) {             // 1. Filtrar
        resultado.add(nome.toUpperCase());  // 2. Transformar
    }
}
Collections.sort(resultado);                // 3. Ordenar

// Tivemos que criar uma lista temporária, escrever loops e controlar o fluxo manualmente.
```

###### Jeito novo (Stream API, Declarativo)
```java
List<String> resultado = nomes.stream()      // Cria a esteira
    .filter(nome -> nome.startsWith("A"))    // Estação 1: Filtra
    .map(String::toUpperCase)                // Estação 2: Transforma
    .sorted()                                // Estação 3: Ordena
    .toList();                               // Final: Empacota numa nova lista
```

----
### Os 3 estágios de um Stream
Um Stream sempre segue essa estrutura de pipeline:

**1. Fonte (Source)**: De onde vêm os dados (uma coleção, um array, um arquivo I/O).

**2. Operações intermediárias**: Processam os dados. Elas são "preguiçosas" (Lazy) - só rodam quando o estágio final é chamado. Elas sempre retornam um novo Stream.
* `.filter()`: Seleciona elementos com base em uma condição (true/false).
* `map()`: Transforma o elemento (ex: converte Objeto -> String, ou String -> Integer, ou também transforma em letras maiúsculas).
* `sorted()`: Ordena os elementos.
* `distinct()`:  Remove duplicatas.

**3. Operação Terminal**: Fecha o Stream, e produz um resultado. O Stream não roda sem isso.
* `collect()`: Transforma o stream em Lista, Set, Map.
* `forEach()`: Executa uma ação para cada item.
* `count()`: Conta quantos elementos sobraram.
* `reduce()`: Combina todos os elementos em um único valor.
