#sap/sap_antigo/sap_pi/componentes_sap_pi/integration_builder/business_system 

```table-of-contents
```
### O que é?
Ele representa um sistema real e identificado no [[System Landscape Directory (SLD)]], funcionando como um sender ou como um receiver de mensagens nos cenários de integração.

Seu maior exemplo, é quando o PI de um determinado cliente possuí um Business System apontado para o ambiente ABAP. Por exemplo,
PI DEV -> ABAP DEV
PI QAS -> ABAP QAS

Na maior parte dos casos, esse Business System já está criado e configurado.

---
### Características
**Representação de sistemas reais**: ele está sempre vinculado a um sistema técnico registrado no [[System Landscape Directory (SLD)]], como um SAP ECC, SAP S/4 HANA ou até aplicações de terceiros.

**Informações detalhadas:** ele armazena dados como versões de componentes de software, instâncias principais, interfaces inbound/outbound disponíveis e outras informações técnicas relevantes para a integração.

**Integração A2A:** é utilizado principalmente em integrações 'application-to-application (A2A)', ou seja, processos internos entre sistemas conhecidos da própria empresa.

**Transporte e mapeamento**: permite transportar objetos de configuração de um ambiente para outro (de DEV para QAS por exemplo), mantendo o vínculo com os sistemas correspondentes em cada ambiente, desde que estejam corretamente mapeados no [[System Landscape Directory (SLD)]].
