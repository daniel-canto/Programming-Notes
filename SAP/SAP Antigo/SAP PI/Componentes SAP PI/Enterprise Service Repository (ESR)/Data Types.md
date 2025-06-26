#sap/sap_antigo/sap_pi/componentes_sap_pi/enterprise_service_repository/data_types  

```table-of-contents
```

### O que é?
Data Types é um objeto do ESR que define a estrutura de dados que serão trocados nas mensagens de integração entre sistemas.
- **Definição Estrutural**: eles especificam os campos e seus respectivos tipos de dados (como string, inteiro, boolean e etc.) que compõem uma mensagem. Portanto, eles funcionam como modelos ou "esqueletos""de dados, descrevendo como a informação deve ser organizada em XML.
- **Criação e Edição**: eles podem ser criados do zero ou baseados em padrões internacionais, como os Core Data Types (CDTs) , Aggregated Data Types (combinam vários CDTs em uma estrutura mais complexa) e Global Data Types (GDTs, que são extensões dos CDTs, com semântica de negócio mais ampla e reutilizáveis em vários contextos).

Portanto, os Data Types apenas **descrevem a estrutura**, eles não são usados diretamente na comunicação, mas sim através de [[Message Types]] e [[Services Interfaces]].
Além disso, essa estrutura é baseado em XML Schema Definition (XSD), portanto a nomenclatura de campos deve obedecer as práticas do XML.

----
### Uso do Data Types
Podemos criar a estrutura do Data Type importando um XSD ou criando na mão. Normalmente,  apenas transformamos o XML para um XSD e depois importamos para o PI, assim a estrutura é gerada de forma mais rápida. No entanto, no PI, os campos devem ser todos `<xsd:element name="nome_campo type="xsd:string" minOccurs="0" />`, com `xsd` e não `xs` ou outra coisa, se não haverá erro.

Para fazer a importação e exportação do XSD de um Data Type, basta ir na aba 'XSD' e selecionar um dos últimos dois botões, localizados na linha do botão 'Execute'.