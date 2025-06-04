#sap/sap_antigo/sap_pi/componentes_sap_pi/enterprise_service_repository/message_types 

```table-of-contents
```

### O que é?
É um objeto que define a estrutura de uma mensagem que será enviada ou recebida em um cenário de integração. Ele serve como uma camada intermediária entre o [[Data Types]] e as [[Service Interface]], encapsulando o [[Data Types]] para uso nas integrações.

Ele pode ser utilizado em interfaces de entrada (inbound) e interfaces de saída (outbound), servindo como base para as mensagens processadas pelo SAP PI.
Assim como o [[Data Types]], ele também pode ser exportado e importado como um arquivo XSD, facilitando a integração e garantindo conformidade.

---
### Uso do Message Type
Para criar o Message Type, antes precisamos ter um [[Data Types]] que será o molde desse Message Type, depois disso, é só criar o objeto no ESR e dentro dele atribuir o [[Data Types]] desejado.
O Message Type será utilizado posteriormente para o [[Message Mapping]], [[Service Interface]], e para alguns objetos do [[Integration Builder]].