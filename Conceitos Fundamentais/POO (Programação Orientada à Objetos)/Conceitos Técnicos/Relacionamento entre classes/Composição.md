#conceitos_fundamentais/poo/conceitos_tecnicos/relacionamento_entre_classes/composicao  

```table-of-contents
```

### O que é
A~={green} composição é um tipo especial de relacionamento "todo-parte" entre classes, onde as partes (componentes) **não existem de forma independente** do todo.=~ Ou seja, se o objeto todo for destruído, automaticamente todas as suas partes também deixam de existir.

----
### O que significa "todo-parte" na composição?

~={green}O “todo” é o objeto principal que **compõe** outros objetos, chamados de “partes”. O ponto fundamental é que **as partes dependem totalmente do todo para existir**=~. Se o objeto “todo” for destruído, as partes também são destruídas, pois não fazem sentido sozinhas.

Por exemplo, pense em um objeto `Casa` composto por vários objetos `Cômodo`. Se a casa for demolida (ou o objeto destruído), os cômodos deixam de existir como entidades independentes. Outro exemplo: um objeto `Pedido` é composto por vários objetos `ItemDePedido`. Se o pedido for excluído, todos os itens associados a ele também são excluídos.

-----
### Como utilizar a composição em código?
A implementação pode variar de acordo com a linguagem, mas a ideia central é que o objeto “todo” cria e gerencia as partes internamente, sendo responsável pela existência e destruição delas.
```Python
classe Pedido
    // Atributos
    privado itens : Lista<ItemDePedido>
    privado numero : Inteiro

    // Métodos
    publico metodo adicionarItem(item: ItemDePedido)
        itens.adicionar(item)
    fim metodo

    publico metodo removerItem(item: ItemDePedido)
        itens.remover(item)
    fim metodo

    // Quando o Pedido é destruído, todos os itens também são destruídos
fim classe

classe ItemDePedido
    // Atributos
    privado descricao : Texto
    privado quantidade : Inteiro
    privado preco : Real
fim classe

```

---
### Resumo
- **Relação forte de dependência:** as partes **não podem ser compartilhadas** entre vários objetos todo e **não existem independentemente** deles.
    
- Composição é usada quando se quer modelar relações em que o “todo” é formado por “partes” que **não têm vida própria** e só fazem sentido dentro do contexto do todo.
    
- Em UML, a composição é indicada por um **losango preto**.
    
Portanto, utilize composição quando as partes só fazem sentido existir junto com o todo e não podem ser reutilizadas ou compartilhadas com outros objetos.