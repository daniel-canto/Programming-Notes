#sap/sap_antigo/sap_pi/componentes_sap_pi/enterprise_service_repository
#topico_nv3 

```table-of-contents
```
### O que é?
É o repositório central onde são definidos e armazenados todos os artefatos de design necessários para a integração entre sistemas no ambiente SAP PI/PO.

---
### Características do ESR
* **Repositório central de objetos de integração**: o ESR contém tipos de dados (Data Types), tipos de mensagens (Message Types), interfaces de serviço (Service Interface), mapeamento de mensagens (Message Mapping) entre outros objetos essenciais para a construção de cenários de integração.
* **Design Time**: o ESR é utilizado na fase de design, ou seja, é onde se modelam e configuram as estruturas e regras das mensagens que serão trocadas entre sistemas. Não é responsável pela execução das integrações, mas sim pelo desenho e documentação das mesmas.
* **Reutilização e Padronização**: o ESR permite a reutilização de objetos padronizados fornecidos pela SAP, como tipos de mensagens e mapeamentos, que podem ser adaptados conforme as necessidades do cliente.

----
### Primeiros passos ao criar um novo projeto
Quando criamos um novo projeto no PI, após criar o produto e a SWC, como vista em [[Criar novo projeto de integração com SWC]], nós precisamos criar os objetos iniciais.
Normalmente, seria esse o fluxo:
1. Desenvolver a estrutura de envio e retorno usando [[Data Types]].
2. Criar [[Message Types]] a partir do [[Data Types]]
3. Criar [[Message Mapping]] de envio para envio, e retorno para retorno (para assegurar integridade de ambas estruturas)
4. Criar [[Service Interface]] para envio e recebimento e definir se a integração será síncrona ou assíncrona.
5. Criar [[Operation Mapping]] referenciando o [[Service Interface]] de envio e retorno, além dos respectivos [[Message Mapping||Message Mappings]].

Normalmente, esse seria o fluxo básico de criação no ESR. Entretanto, isso pode variar para cada caso, portanto na seção de [[Técnicas SAP PI]], podemos ver exemplos de criação de projeto do 0 em diferentes cenários de integração.

---
### Descrição dos objetos do ESR
Aqui, estarão listados os objetos do ESR com suas características e opções.

[[Data Types]]
[[Message Types]]
[[Message Mapping]]
[[Service Interface]]
