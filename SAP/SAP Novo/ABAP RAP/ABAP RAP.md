#sap/sap_novo/abap_rap
#topico_nv1 


```table-of-contents
```
### O que é?
O ABAP RESTful Application Programming Model é um modelo de desenvolvimento criado pela SAP, que visa simplificar a criação de aplicações empresariais modernas no SAP S/4 HANA e no [[SAP BTP]].  Ela fornece uma estrutura padronizada baseada em princípios REST para o desenvolvimento das aplicações.


---
### Conceitos teóricos do ABAP RAP
###### BO (Business Object)
O BO consiste em uma árvore hierárquica, onde cada galho é unido através de uma associação chamada _composition_ (composição). A raiz dessa árvore é o _root entity_, que serve como representação do **BO. Ele é um _service agnostic_ (serviço agnóstico), pois não importa se é um OData v2 ou OData v4. Exemplo:
![[Pasted image 20250730152427.png]]

###### Behavior of Business Object
Esse conceito seria basicamente o que o BO pode fazer, ou seja, o Behavior seria as ações do BO, como o CRUD por exemplo. Ou seja, como a própria tradução diz, seria o comportamento do BO. Ele é criado usando Behavior Definition Language (BDL), e é possível colocar todo esse comportamento em apenas um arquivo, esse seria o conceito de “_One root entity (BO) = One Behavior Definition)_. Vamos usar o exemplo da casa novamente:

![[Pasted image 20250730152514.png]]
Nessa imagem, estaria todo o comportamento do BO, sendo cada função declarado passo a passo. Até mesmo o comportamento dos galhos deverão estar no mesmo arquivo.

Podemos ter dois tipos de Behavior Defintion. **Unmanaged** e **Managed.** Quando colocamos um behavior definiton como **managed**, estamos habilitando um framework que basicamente irá criar uma lógica para nós. Ele já vem com algumas funções prontas para implementação, como o CRUD. Ele é utilizado quando não se tem uma lógica de negócio e você deseja criar essa lógica de forma automática. Porém, o **unmanaged** é o oposto, você deverá criar a lógica de negócio, sem implementações automáticas do _framewok_.

###### EML vs BDL
Em uma Behavior Definition, podemos inserir lógica customizada para criar processos para determinado objetivo no nosso sistema. Isso é feito através do EML (Entity Manipulation Language). A principal **diferença** **entre o BDL e o EML** é que o **BDL** é focada na definição declarativa dos comportamentos e regras de negócio a nível de modelo, enquanto que o **EML** é focada na manipulação dessas entidades de negócio a nível de código. Em resumo, uma é usada para definir os comportamentos, e a outra é usada para construir esses comportamentos.

###### Custom Logic usando EML em um Behavior Definiton
Podemos criar uma lógica customizada com o EML. Normalmente, usamos o BDL para definir esses processos. O EML fica localizado dentro de uma classe que a Behavior Definition implementou, com isso, criamos métodos nessa classe em EML (ela lembra muito o ABAP em nível de código) e o Behavior Definition chama esse método, normalmente sendo em uma _determiantion_, _validation_ ou _action_. Essa classe sempre é declarada dessa forma: `implementation in class <nomeClasse> unique`

Normalmente, o EML tem 3 declarações principais, sendo elas o _modify_, _read_ e o _commit_.

###### Service Definiton
É aqui que podemos expor as entidades CDS em conjunto ou separadamente. Como dito anteriormente, ele continua sendo _server-agnostic,_ ou seja, podemos usar tanto OData v2 ou OData v4.
###### Service Binding
Pela primeira vez no modelo RAP, há algo que não é _server-agnostic_, aqui, vamos pegar a Service Definition e conectar com o _client-server_ através de um protocolo OData, sendo o v2 ou v4.