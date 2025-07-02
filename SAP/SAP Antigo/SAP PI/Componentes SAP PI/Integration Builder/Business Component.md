#sap/sap_antigo/sap_pi/componentes_sap_pi/integration_builder/business_component 

```table-of-contents
```

### O que é?
Ele é um objeto que representa uma unidade abstrata de comunicação, usada para endereçar senders e receivers de mensagens em cenários de integração. Ele é útil quando você precisa configurar integrações com sistemas cujos detalhes técnicos não são conhecidos ou não estão registrados no [[System Landscape Directory (SLD)]].

---
### Principais características
**Abstração**: diferente do [[Business System]], que representa um sistema real e registrado no [[System Landscape Directory (SLD)]], o Business Component é uma entidade lógica ou abstrata. Ele é utilizada quando não se deseja ou não se expor detalhes do sistema técnico.

**Agrupamento de interfaces:** permite agrupar as interfaces públicas (inbound e outbound) que serão usadas na comunicação, facilitando a organização e gerenciamento.

**Configuração flexível:** pode ser criado e configurado diretamente no Integration Directory, podendo ser associado a uma [[Party]].

**Uso em cenários B2B:** é a escolha padrão para cenários entre empresas, onde normalmente só as interfaces são conhecidas e compartilhadas, não os detalhes do ambiente técnico do parceiro.

**Atribuir communication channels:** é possível criar e associar [[Communication Channel]] ao Business Component, definindo como as mensagens serão enviadas ou recebidas.

