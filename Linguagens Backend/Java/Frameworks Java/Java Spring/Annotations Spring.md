#backend/java/frameworks_java/java_spring/annotations_spring 

```table-of-contents
```

### O que é?


### Annotations

#### @Autowired
Ele ativa a [[Injeção de Dependência]], onde apenas declaramos o `@Autowired` em cima do atributo de uma classe por exemplo e utilizamos ela como uma instância. Basicamente abstrai a necessidade de utilizar  o `Object = new Object`. Muito utilizado para injetar as dependências de um Repository em um Service no spring, para manipularmos seus dados.

#### @Valid
É uma annotations originada do [[Jakarta]], feita principalmente para validar de forma simples os campos que uma API recebe, utilizando annotations relacionas como @NotNull e @Email. Para fazer isso, veja a anotação [[Validação de campos com @Valid]].
