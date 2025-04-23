#conceitos_fundamentais/poo/pilares_da_poo/heranca 

### O que é?
~={green}A herança em POO permite basear uma nova classe na definição de uma classe previamente existente (que seria a sua mãe)=~.
Em outras palavras, podemos fazer uma classe herdar os atributos (características) e os métodos (ações) de outras classes, criando um relacionamento de mãe e filha, onde a filha quem herda esses dados. Com isso, podemos herdar essas características e adicionar novas para tornar a classe objetiva.

----
### Exemplo de herança em UML
Em UML, a herança seria assim:
* Imagem
	![[Pasted image 20250423162440.png]]

No caso, a classe "Professor" ficaria no mesmo nível que a "Aluno" e a "Funcionário", porém não deu por falta de espaço.
Mas como podemos ver, conseguimos diminuir a complexidade e repetição de dados com a herança, pois com a herança, subtende-se que as 3 classes abaixo possuem as mesmas características de pessoa.

----
### Em código
Normalmente, em linguagens de programação com POO, utilizamos o "estende" para indicar que a classe está herdando outra classe, por exemplo:
```python
classe Aluno estende Pessoa
```
Porém, isso varia de acordo com a sintaxe da linguagem.

Uma boa prática, seria sempre [[Encapsulamento|encapsular]] as classes com [[Métodos e Atributos#Métodos Acessores (Encapsulamento)|métodos acessores]]. Se a classe mãe conter métodos getter e setter para seus atributos, ao instanciar um objeto de uma classe filha, utilizamos os atributos herdados normalmente. No caso do UML acima, se fossemos colocar um nome (atributo da classe mãe) seria escrita normalmente, por exemplo:
```python
p1 = new Aluno()
p1.setNome("Pedro")
```
Ou seja, mesmo o atributo não sendo diretamente da classe filha, seu uso continua sendo o mesmo, pois a herança deixa as características implícitas.

----
### Navegação pela herança
- Imagem
	![[Pasted image 20250423173435.png]]

----
### Tipos de herança
Existem dois tipos principais de herança em POO.

##### Herança de implementação
É quando uma classe herda tanto a estrutura (atributos e métodos) quanto a implementação dos métodos da superclasse (classe mãe). Normalmente a superclasse é uma [[Classes, Objetos e Instâncias#O que é uma classe abstrata?|classe abstrata]].

