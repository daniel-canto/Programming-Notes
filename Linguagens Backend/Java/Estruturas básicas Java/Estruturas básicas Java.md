#backend/java/estruturas_basicas_java 

Aqui estão listados as estruturas básicas de Java.

```table-of-contents
```

### For Each
Para fazermos um For Each em Java, podemos fazer o seguinte código:
```java
import java.util.ArrayList;  
  
public class Main {  
    public static void main(String[] args) {  
        ArrayList<String> nomes = new ArrayList<>();  
        nomes.add("Daniel");  
        nomes.add("Bruno");  
        nomes.add("Roberto");  
        nomes.add("Mariana");  
  
        var i = 0;  
        for (String nome : nomes) {  
            i++;  
            System.out.println("Nome: " + i + " " + nome);  
        }  
    }  
}
```
Normalmente ele é muito utilizado com [[Array|arrays]].