#conceitos_fundamentais/poo/conceitos_tecnicos/relacionamento_entre_classes/agregacao  

```table-of-contents
```

### O que é
Em POO, a agregação é um tipo de relacionamento entre classes conhecido como ~={green}"todo-parte"=~. ~={green}Isso significa que uma classe (o "todo") é formada por uma ou mais instâncias de outra classe (as "partes"), mas essas partes podem existir independentemente do todo=~.

----
### O que significa "todo-parte" na agregação?
~={green}O "todo" seria o objeto principal que agrega outros objetos, chamados de "partes"=~. O ponto fundamental é que ~={green}as partes não dependem do todo para existir. Ou seja, se o objeto "todo" for destruído, as partes continuam existindo=~.
Por exemplo, uma biblioteca pode agregar vários livros, se a biblioteca for fechada (ou o objeto for destruído), os livros ainda podem existir e serem agregados a outras bibliotecas ou coleções. Outro exemplo, poderia ser um time que agrega vários jogadores, se o time for desfeito, os jogadores continuam existindo e podem ser agregados a outros times.

----
### Exemplo de agregação em UML
* Imagem:
	![[Pasted image 20250422144721.png]]
Na imagem acima, temos um exemplo de agregação usando as classes Lutador e Luta.
Nesse caso, um objeto da classe Lutador seria uma parte, pois ele é um individuo que existe independentemente da luta, enquanto o objeto da classe Luta seria o todo, pois ele precisa agregar dois lutadores para que o objeto exista, por isso sempre o todo contém as partes e as partes podem existir mesmo sem o todo.
Além disso, temos uma multiplicidade nesse uml. 
O Lutador pode disputar zero ou mais lutas, por isso o 0..* 
A Luta precisa ter obrigatoriamente 2 lutadores, por isso o uso do * 

----
### Como utilizar a agregação em código?
Claro que cada linguagem tem a sua implementação única pela diferença de sintaxe, mas geralmente a base é a mesma. Portanto, usarei algoritmos e o UML acima para demonstrar essa técnica.
``` Python
classe Luta
    // Atributos
    privado desafiado : Lutador
    privado desafiante : Lutador
    privado rounds : Inteiro
    privado aprovada : Lógico

    // Métodos
    publico metodo marcarLuta()
        (...)
    fim metodo

    publico metodo lutar()
        (...)
    fim metodo

    // Métodos Especiais
    publico metodo setDesafiado(dd: Lutador)
        desafiado = dd
    fim metodo

    publico metodo getDesafiado()
        retorne desafiado
    fim metodo
    (...)
fim classe

```
Como estamos dizendo que o todo irá receber um objeto parte, precisamos que o respectivo atributo do todo receba o tipo do objeto da parte. Por exemplo, ~={green}o atributo "desafiado" recebe um dado do tipo do objeto da classe Lutador, e o mesmo ocorre com o "desafiante".=~ ~={pink}Em cenários que temos mais de um objeto sendo enviado no mesmo campo, podemos fazer um array que vai receber vários objetos de uma determinada classe parte=~.

----
### Resumo
* **Relação fraca de dependência:** as partes podem ser compartilhadas entre vários objetos todo e existem independentemente deles.
Portanto, agregação é usada quando se quer modelar relações em que o “todo” é formado por “partes”, mas essas partes têm vida própria e podem ser compartilhadas ou existir fora do contexto do todo.