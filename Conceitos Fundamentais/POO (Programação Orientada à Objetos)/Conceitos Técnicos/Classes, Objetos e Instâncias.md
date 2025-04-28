#conceitos_fundamentais/poo/conceitos_tecnicos/classes_objetos_e_instancias 


Aqui falaremos sobre o começo de POO, que seria sobre as classes, objetos e instâncias.

```table-of-contents
```

### O que é um objeto?
~={green}Tudo aquilo que possuí uma característica, comportamento e estado, é um objeto.=~ Um compromisso por exemplo, poderia ser representado por um objeto em programação, pois ele possuí características (como data, local e com quem é esse compromisso), seus comportamentos poderiam ser marcar, desmarcar, adiar, e seu estado poderia ser combinado, adiado, remarcado e etc.  

##### Exemplos de objetos
Vamos fazer dois exemplos de objetos, um objeto físico e um objeto abstrato.

**Objeto Físico - Caneta**

| **~={yellow}Características (Atributos)=~** |
| :-----------------------------------------: |
|                   Modelo                    |
|                     Cor                     |
|                   Tampada                   |
|                    Carga                    |
|   ~={yellow}**Comportamento (Métodos)**=~   |
|                  Escrever                   |
|                  Rabiscar                   |
|                   Pintar                    |
|                   Tampar                    |
|                  Destampar                  |

**Objeto abstrato - Compromisso**

| **~={yellow}Características (Atributos)=~** |
| :-----------------------------------------: |
|                    Local                    |
|                    Data                     |
|                   Pessoa                    |
|                   Motivo                    |
|   ~={yellow}**Comportamento (Métodos)**=~   |
|                   Marcar                    |
|                  Desmarcar                  |
|                  Remarcar                   |

----
### O que é uma classe?
Uma classe é como se fosse um ~={green}molde para poder criar um objeto=~.
Portanto, quando criamos uma classe simples de um objeto, normalmente criamos seus atributos, passamos o tipo de cada atributo e depois criamos seus métodos.
Por exemplo, se criamos uma classe Caneta com todos os atributos e métodos que representam uma caneta, a classe estará pronta para criar uma [[Classes, Objetos e Instâncias#O que é uma instância?|instância]] de uma classe, assim gerando um novo objeto.
Para saber mais sobre métodos e atributos, clique aqui: [[Métodos e Atributos]]

##### O que é uma classe abstrata?
~={green}Uma classe abstrata não pode ser instanciada=~, portanto ela não pode gerar um objeto. ~={green}Ela só serve como classe mãe ou progenitora=~, como visto em [[Herança]]. Ela pode conter métodos implementados (com código) e [[Métodos e Atributos#Método Abstrato|métodos abstratos]] (sem código, apenas a assinatura, obrigando as subclasses a implementarem seu código)

##### O que é uma classe final?
~={green}É uma classe que não pode ser herdada por outra classe=~. Ela precisa ser obrigatoriamente uma folha, como visto em [[Herança#Navegação pela herança]].

---
### O que é uma instância?
Um instância é ~={green}quando criamos um novo [[Classes, Objetos e Instâncias#O que é um objeto?|objeto]] através de uma classe=~. Apesar de nós termos criado uma classe para moldar uma caneta, cada caneta pode ser individualmente única.
Por exemplo, podemos criar dois objetos de instância da classe caneta: a caneta azul e a caneta preta.
Ambas possuem as mesmas exatas funções e atributos, porém seus valores podem ser diferentes, por exemplo, a caneta azul possuí o atributo cor como azul, enquanto a caneta preta possuí o atributo cor como preto. São a mesma classe de objeto (uma caneta), mas com características diferentes (nesse caso a cor)

