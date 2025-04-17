#conceitos_fundamentais/poo/conceitos_tecnicos/interfaces 

```table-of-contents
```
### O que é?
As interfaces seriam como uma lista de serviços fornecidos por um componente. É o contato com o mundo exterior, que define o que pode ser feito com um objeto dessa classe.
Exemplificando, elas funcionam como um contrato, onde ~={green}elas definem um conjunto de métodos (assinaturas) que uma classe deve obrigatoriamente implementar se quiser "assinar" essa interface (contrato)=~.
~={green}Esse conceito é muito atrelado ao conceito de [[Encapsulamento]], pois as interfaces facilitam a comunicação da lógica externa com a lógica interna de uma classe=~.

### Características
* **Contrato de métodos**: uma interface declara métodos, mas não implementa nenhum deles, esse é o papel das classes, onde elas fornecem o código desses métodos.
* **Sem atributos de instância**: elas geralmente não possuem atributos de instância (variáveis que guardam estado), apenas constantes, se necessário.
* **Não podem ser instanciadas**: você não pode criar um objeto diretamente de uma interface, ela serve apenas como base para outras classes.
* **Implementação múltipla**: uma classe pode implementar várias interfaces ao mesmo tempo, resolvendo limitações como herança múltipla.
* **Abstração**: elas ajudam a separar a definição do que um objeto vai fazer (a interface) da forma como ele faz (a implementação).

### Qual seu objetivo?
* **Padronizar**: garantem que diferentes classes ofereçam os mesmos métodos, mesmo que a implementação interna seja diferente.
* **Polimorfismo**: permitem tratar objetos de diferentes classes de maneira uniforme, se eles implementarem a mesma interface.
* **Baixo acoplamento**: facilitam a troca de implementações sem alterar o código que usa a interface, tornando o sistema mais flexível e fácil de manter.