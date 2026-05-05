#backend/java/conceitos_e_recursos/java_collection 
#topico_nv2 

```table-of-contents
```

### O que é?
É um conjunto padronizado de interfaces e classes fornecido pela linguagem Java, usado para representar e manipular grupos de dados (objetos) de forma eficiente e organizada.
Assim, ao invés de criarmos as estruturas do zero, o Collections Framework oferece implementações prontas para uso que cobrem grande parte das necessidades de manipulação de dados.
Uma das vantagens de se utilizar essa abordagem, é que podemos trocar as classes caso seja necessário, sem trocar o tipo. Por isso, utilizar essas interfaces é uma boa prática.
Entretanto, uma desvantagem é a impossibilidade de utilizar métodos da própria classe concreta.

---
### Como funciona?
De forma simplificada, as interfaces (List, Set, Map, Queue) definem o contrato (assinatura de métodos em uma interface) que devem implementar e ser considerada um certo "tipo" de coleção. Por exemplo, a classe ArrayList implementa a interface List.

----
### Interfaces
Essa biblioteca é composta por 4 elementos principais:

###### List
É uma ~={green}coleção ordenada que permite elementos duplicados=~. Os elementos são acessados por índice.
**Exemplos de classes:** ArrayList, LinkedList e Vector.

###### Set
É uma coleção que~={green} não permite elementos duplicados e não tem ordem garantida=~.
**Exemplos de classes**: HashSet, LinkedHashSet e TreeSet.

###### Queue (Fila)
Coleção usada para armazenar elementos antes do processamento, normalmente seguindo o FIFO (First In, First Out).

###### Map
Embora não herde da interface principal `Collection`, é considerada parte da biblioteca. ~={green}Armazena dados no formato chave-valor, onde cada chave deve ser única=~. Seriam como os objetos do JS ou os [[Dicionários| dicionários]] em Python.
**Exemplos de classe:** HashMap, TreeMap e LinkedHashMap.

----
### Classes tipo List

##### ArrayList
Como já mencionado em [[Array]], o `ArrayList` seria uma lista que pode ser manipulada à vontade, podendo adicionar, remover e ler elementos dessa lista.
Aqui, podemos inferir o tipo de referência da interface `List` para essa classe, assim padronizando a classe.
É importante ressaltar que, caso algum método específico do `ArrayList` precise ser utilizado, é obrigatório instanciar a classe inferindo o seu próprio tipo de referência.

```java
package introducao_java;  
import java.util.ArrayList;  
import java.util.List;  
  
public class Main {  
    public static void main(String[] args) {  
        List<String> minhaLista = new ArrayList<>();  
  
        minhaLista.add("teste");  
        String res = minhaLista.get(0);  
        System.out.println(res);  
    }  
}
```

---
### Classes tipo Set
##### HashSet
É uma classe que serve para armazenar um conjunto de elementos únicos, sem nenhuma ordem garantida. Essa classe é a importação mais popular da interface [[Java Collection#Set|set]].
O uso principal dessa classe é garantir que não haja duplicatas em uma coleção, ao mesmo tempo que oferece um desempenho muito rápido para operações básicas.
Ela armazena os elementos usando um mecanismo chamado [[Hash Table]], permitindo que operações de busca, inserção e remoção sejam executados em tempo quase constante (geralmente O(1) na maioria dos casos), sendo extremamente rápido. 
Exemplo de uso:
```java
import java.util.Set;  
import java.util.HashSet;

Set<String> nomes = new HashSet<>();  
nomes.add("Daniel");  
nomes.add("João");  
System.out.println(nomes.contains("Daniel")); // É exibido true, pois esse valor existe no Set.
```

----
### Classes tipo Map
##### HashMap
É a classe mais comum e fundamental da interface [[Java Collection#Map|map]], pois serve para armazenar dados em pares de chave-valor.
Assim como HashSet, por utilizar o [[Hash Table]], essa é uma estrutura bem rápida contendo O(1) em grande parte dos casos, pois ele encontra o valor diretamente sem percorrer toda a estrutura.
Exemplo de uso:
```java
import java.util.Map;  
import java.util.HashMap;

Map<String, String> map = new HashMap<>();  
map.put("nome", "Daniel G.");  
System.out.println(map.get("nome"));
```

---
### Classes tipo Queue
##### LinkedList
É uma classe que implementa a interface queue, diferente do [[Java Collection#ArrayList|ArrayList]], que usa um [[Array]] dinâmico, o LinkedList usa uma estrutura de lista duplamente encadeada. Que segue o conceito de [[Lista Encadeada]].
Exemplo de uso:
```java
Queue<String> fila = new LinkedList<>();  
fila.add("Daniel");  
fila.add("Bruno");  
  
System.out.println("Fila: " + fila.poll());  
System.out.println("Fila: " + fila.poll());
```
Aqui criamos uma fila encadeada, onde o primeiro elemento a ser processado seria o `Daniel`. Para isso, utilizamos o método da Queue chamado `poll()`, responsável por pegar o próximo elemento da lista, passar seu valor para a variável ou `println` e remover o valor da lista, para passar para o próximo. Ao invés do `poll()`, podemos utilizar o `remove()`, que faz a mesma coisa, mas caso não tenha nenhum elemento na fila, ele lança uma exceção.