#sap/sap_antigo/sap_pi/componentes_sap_pi/integration_builder/integrated_configuration 

```table-of-contents
```

### O que é?
Esse é um objeto de configuração utilizado para definir, em um único lugar, todo o fluxo de integração de ponta a ponta quando a comunicação ocorre **exclusivamente** via Advanced Adapter Engine (AAE). Ele substitui o modelo clássico, onde precisavámos criar vários objetos separados ([[Sender Agreement]], [[Receiver Determination]], [[Interface Determination]] e [[Receiver Agreement]]), assim simplificando o desenvolvimento.

----
### Características 
**Unificação**: permite configurar todo o cenário de integração em um único objeto, reduzindo a complexidade e facilitando a manutenção.

**Desempenho:** o fluxo é mais rápido e eficiente, pois elimina a passagem pelo Integration Engine ABAP.

**Escopo:** é utilizado principalmente para integrações locais (cenários Java-only), onde todos os adaptadores são suportados pelo AAE.

---
### Processo de criação
1. Selecione o [[Business Component]] do sender, a [[Service Interface]] e o namespace.
2. Define o canal de entrada (inbound) para receber as mensagens.
3. Especifica o(s) receptor(es) e o canal de saída (outbound) para envio das mensagens.
4. Configure o [[Operation Mapping]], caso seja necessário transformar a mensagem entre os formatos de entrada e saída.
5. Salve e ative o objeto.