#sap/sap_antigo/sap_pi/componentes_sap_pi/system_landscape_directory
#topico_nv3 

```table-of-contents
```

### O que é?
O SLD (System Landscape Directory) no SAP PI é um componente central e fundamental do ambiente SAP, pois é responsável por gerenciar e armazenar informações detalhadas sobre todos os sistemas e componentes que fazem parte do landscape SAP de uma organização.
* Ele funciona como um repositório central que descreve todos os sistemas (SAP e não-SAP), servidores, produtos, versões de componentes de software e suas relações dentro do ambiente de TI.
* Ele mantém informações técnicas (como endereços de rede, tipos de sistemas, clientes, etc.) e informações de negócios (como sistemas de negócios e agrupamentos de sistemas).
* Ele é essencial para a integração eficiente entre sistemas, pois permite que o SAP PI/PO reconheça e se comunique com todos os sistemas do landscape, facilitando o roteamento e monitoramento das mensagens de integração.

### Estrutura e categorias
O SLD organiza as informações em 3 grandes categorias principais:
- **Landscape**: permite  você visualizar e configurar sistemas técnicos, landscapes (grupos de sistemas) e sistemas de negócios.
- **Software Catalog**: contém informações sobre produtos SAP e componentes de software instalados.
- **Development**: gerencia reservas de nomes e dados no nível CIM (Common Information Model). importante para o desenvolvimento e integração.

### Funções do SLD
Abaixo, está uma lista com possibilidades de uso para o SLD.

[[Criar novo projeto de integração com SWC]]