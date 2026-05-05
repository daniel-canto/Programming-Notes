#backend/java/bibliotecas/jakarta  
#topico_nv3 

```table-of-contents
```

### O que é?
Apesar de ser listada como uma biblioteca, na verdade o Jakarta é um conjunto de especificações para desenvolvimento Java Enterprise, onde o Jakarta define as especificações e outras bibliotecas/frameworks implementam.

Portanto, o Jakarta possuí diversas especificações para casos de uso diferentes:
* **Jakarta Servlet**
* **Jakarta Restful Web Services**, sendo utilizado pelo RESTEasy e Jersey.
* **Jakarta Websocket**, sendo usado para utilização do [[Websocket|websocket]]
* **Jakarta CDI para injeção de depêndencias**
E muito mais.

Portanto, o Jakarta se torna uma base para grandes frameworks, como o [[Java Spring]] e o [[Java Spring JPA e Hibernate]].

De forma **resumida** o Jakarta funciona como uma biblioteca de contratos (interfaces, annotations e specifications) que definem o que deve existir, deixando para os frameworks como [[Hibernate]], [[Jersey]] e [[Java Spring|Spring]] a responsabilidade de definir como funciona.

----
### Relação entre Jakarta e Spring
O Spring Boot não é uma implementação do Jakarta, mas ainda sim ele conversa com ele em vários pontos:
* Jakarta Persistence (JPA): Spring Data JPA usa o **Hibernate** que implementa o JPA.
* Jakarta Transactions: A annotation [[Annotations Spring|@Transactional]] usa o JTA por baixo dos panos.
* Jakarta Servlet: usado pelo Spring MVC.
* Jakarta CDI: O Spring usa para seu próprio sistema de DI (Dependency Injection) com o [[Annotations Spring#@Autowired|@Autowired]].
* Jakarta Bean Validation: O spring usa para validar campos em DTOs, com as annotations [[Annotations Spring#@Valid|@Valid]] e [[Annotations Spring#@NotNull|@NotNull]] para a validação de seus campos de forma abstraída e simples, como visto em [[Validação de campos com @Valid]].
