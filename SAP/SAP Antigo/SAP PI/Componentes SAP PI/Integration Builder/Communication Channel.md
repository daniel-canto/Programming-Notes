#sap/sap_antigo/sap_pi/componentes_sap_pi/integration_builder/communication_channel 

```table-of-contents
```
### O que é?
É o objeto responsável por configurar a comunicação técnica entre o SAP PI e sistemas externos ou internos, definindo como as mensagens serão enviadas ou recebidas por meio de adaptadores específicos, como REST e SOAP.

Portanto, ele define como e por qual protocolo (como File, FTP, HTTP, IDoc, SOAP, JDBC, etc.) o SAP PI irá se conectar a outros sistemas.
Cada Communication Channel é sempre associado a um [[Business Component]] e pode ser do tipo sender ou receiver, dependendo da direção do fluxo de mensagens.

---
### Principais parâmetros
**Tipo de adapter:** define o protocolo e adaptador utilizado (ex: REST com formato JSON.)
**Direção:** indica se o canal é de envio ou recebimento.
**Configurações específicas:** parâmetros como diretórios, endereços, autenticação, formatos de mensagem, entre outros.

---
### Processo de criação
1. Defina o [[Business Component]] ao qual o canal estará vinculado.
2. Escolha o tipo do canal, sender ou receiver.
3. Selecione o tipo de adapter desejado e configure os parâmetros necessários para o cenário.
4. Salve e ative o canal.

----
### Monitoramento e controle
Os Communication Channels podem ser monitorados no PI, através do PI NWA.