#backend/java/conceitos_e_recursos/generics 

```table-of-contents
```

### O que é?
É um recurso da linguagem Java introduzido na versão 5, que permite que ~={green}classes, interfaces e métodos operem com tipos de dados especificados como parâmetros=~ durante a criação ou uso. Eles permitem que você escreva códigos mais seguros em termos de tipagem (type-safe) e reutilizável, pois os Generics transformam erros de execução em erros de compilação.

Por exemplo, antes dos generics, as [[Java Collection|classes de coleções]] operavam com objetos do tipo genérico `Object`, com isso, havia um grande risco de exceção em runtime e a necessidade de casting manual, pois antes em uma ArrayList por exemplo, você conseguia colocar diferentes tipos de dados em cada índice. Com isso, ao obter o valor de um índice, poderia gerar um erro, pois o tipo estava diferente.

Agora, com o Generics, você especifica o tipo dos objetos que a coleção irá armazenar, geralmente usando `<>`. Como é o caso da declaração de um [[Java Collection#ArrayList|ArrayList]] atualmente.

---
### Benefícios
1. **Segurança de Tipo em Runtime (Type Safety):** o compilador verifica se você está usando o tipo correto.
2. **Eliminação de Casts:** não é mais necessário utilizar casts manuais ao recuperar dados da coleção, tornando o código mais limpo.
3. **Reutilização:** você pode escrever uma única classe ou método que funciona com diferentes tipos, como é o caso das classes de coleções como o ArrayList.

----
### Como usar
Ao definir suas classes ou métodos que usam Generic, por boa prática, você usa letra maiúsculas para representar o tipo, dessa forma:

**E** (Elemento), usado para elementos em coleções; `List<E>`.
**K** (Chave), usado em mapeamentos; `Map<K, V>`.
**V** (Valor), usado em mapeamentos; `MAP<K, V>`.
**N** (Número), usado para números.
**T** (Tipo), usado para tipos genéricos; `T result = get(T input).

##### Exemplo de uso
Aqui definimos a classe que aceita tipos genéricos.
```java
public class Caixa<T> {
	private T conteudo;
	
	public void setConteudo(T conteudo) {
		this.conteudo = conteudo;
	}
	
	public T getConteudo {
		return conteudo;
	}
}
```

Agora, poderíamos utilizar essa classe dessa forma:
```java
public classe Main {
	public static void main(String[] args) {
		Caixa<String> caixaDeTexto = new Caixa<>();  
		caixaDeTexto.setConteudo("Documento Importante");  
		  
		Caixa<Integer> caixaDeNumeros = new Caixa<>();  
		caixaDeNumeros.setConteudo(2025);  
		  
		System.out.println(caixaDeTexto.getConteudo());  
		System.out.println(caixaDeNumeros.getConteudo());
	}
}
```

### Wildcards (Curingas) - Sinal `?`.
Às vezes, você que flexibilidade para aceitar "qualquer lista", mas com limitações. Para isso, usamos o `?`.
`List<?>`: Lista de qualquer coisa, geralmente apenas para leitura.
`List<? extends Number>`: Lista de qualquer coisa que seja filha de Number (Integer, Double, Float).