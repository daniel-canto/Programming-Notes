#backend/java/estrutura_de_dados/array  

```table-of-contents
```

Em Java, temos dois "tipos" de arrays diferentes, o Array e o Array List, que vamos abordar abaixo.

### O que é o Array
Em Java, o termo "Array" seria uma lista com tamanho predefinido e limitado, ou seja, ele não é dinâmico, assim ele não suporta a adição de novas posições durante o processamento.
Abaixo, segue um exemplo de uso desse array:
```java
public class Main {  
    public static void main(String[] args) {  
       
        // Definindo um array com apenas 3 posicoes com valores padrão.  
        int[] arrayInteiros = {1,2,3};  
          
        // Definindo um array com apenas 5 posicoes, sem valores padrão.  
        int[] arrayInteiros5MAX = new int[5];  
  
        arrayInteiros5MAX[2] = 10;  
  
        System.out.println(arrayInteiros5MAX[2]);  
    }  
}
```

Portanto, esse é um array mais simples, por não haver escalonamento. Nesse array, podemos usar o atributo `length` para obter a quantidade de posições desse array, dessa forma:
```java
System.out.println(arrayInteiros5MAX.length);
```
Note que isso é um atributo, e não um método ou função.

### O que é o Array List
O Array List por sua vez, seria um array dinâmico, possuindo diversos métodos auxiliares para facilitar a sua manipulação, como o `get()` que obtém o valor de um índice.
Diferentemente do array convencional, este precisamos importar a sua classe no nosso código, segue abaixo um exemplo mais completo para a sua utilização básica:
```java
import java.util.ArrayList;  
  
public class Main {  
    public static void main(String[] args) {  
        ArrayList<String> lista = new ArrayList<>();  
        lista.add("Teste lista dinâmica.");  
  
        System.out.println(lista.get(0));  
    }  
}
```