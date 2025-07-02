#sap/sap_antigo/sap_pi/componentes_sap_pi/enterprise_service_repository/operation_mapping

```table-of-contents
```

### O que é?
É um objeto responsável por relacionar uma operation de uma [[Service Interface]] de entrada com uma operation de saída, definindo qual programa de mapeamento será executado para transformar a mensagem entre esses dois pontos durante o processo de integração.

Ele serve para especificar como os dados enviados devem ser convertidos para o formato aceito pelo sistema destinatário, utilizando um ou mais programas de mapeamento (pelo [[Message Mapping]], [[Imported Archives (Java Mapping)]] ou [[XSLT Mapping]]). Além disso, ele garante que a operation correta seja mapeada para a operação correta da interface de destino, inclusive em cenário com múltiplas operations ou mensagens complexas.
Por fim, ele também pode ser usado para mensagens síncronas, assíncronas, solicitações, respostas ou mensagens de erro.

---
### Processo de criação
1. Selecione as [[Service Interface]] de origem e destino.
2. Associe os mapeamentos de mensagem apropriados para requisições, respostas e/ou falhas.
3. Salve a ative o objeto.