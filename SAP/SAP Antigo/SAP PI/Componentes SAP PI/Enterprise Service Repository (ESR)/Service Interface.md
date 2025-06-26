#sap/sap_antigo/sap_pi/componentes_sap_pi/enterprise_service_repository/service_interface 

```table-of-contents
```

### O que é?
É um objeto que define o conjunto de operações (serviços) que serão disponibilizados ou consumidos em um cenário de integração. Ele representa o "contrato" de comunicação entre sistemas, especificando quais mensagens podem ser enviadas ou recebidas, seus formatos e padrões de comunicação.

### Características
* **Grupo de operações**: um SI que agrupa uma ou mais operações (como um CRUD), cada uma delas é associada a mensagens de entrada e saída com [[Message Types]].

* **Independência da plataforma**: o design da interface é independente de linguagem de programação ou sistema operacional, permitindo integração entre sistemas heterogêneos.

* **Direção de comunicação**: pode ser definida como inbound (entrada), outbound (saída) ou abstrata, que é usada em processos de orquestração, sem direção fixa.

* **Padrão de comunicação**:  suporta comunicação assíncrona (apenas envio ou recebimento da mensagem) e comunicação síncrona (requisição e resposta).

* **Reutilização**: elas podem ser reutilizadas em diferentes cenários.

### Tipos de Service Interface
+ **Inbound (entrada):** interface que recebe mensagens no SAP PI.
+ **Outbound (saída)**: interface que envia mensagens a partir do SAP PI.
+ **Abstract (abstrata)**: interface usada em processos de integração (orquestração), sem direção definida, geralmente em processos BPM ou cenários de mediação.

### Uso do Service Interface
![[Pasted image 20250604152428.png]]
Na imagem acima, podemos ver um exemplo de Service Interface para envio de dados, onde temos mais de uma operação, onde cada uma possuí um [[Message Types]] diferente, tanto de envio quanto de retorno.