#sap/sap_antigo/sap_pi/componentes_sap_pi/integration_builder 

```table-of-contents
```

### O que é?
É uma aplicação baseada em Java que oferece uma interface gráfica unificada para criar, configurar e gerenciar todos os componentes necessários para integrações entre sistemas.

----
### Características
**Desenvolvimento de integrações:** ele serve para criar soluções completas de integração, permitindo conectar sistemas SAP com outros sistema SAP ou não-SAP. Aqui você define como os dados fluem entre esses sistemas.

**Configuração de cenários:** permite configurar cenários específicos de negócio, como sincronização de dados de clientes entre um sistema CRM e um ERP ou uma integração de pedidos de vendas entre filiais de uma empresa.

**Transformação de dados:** permite a criação de mapeamentos que transformam dados em um formato para outro, como converter um XML para JSON para a comunicação entre os sistemas.

----
### Primeiros passos ao criar um novo projeto
Após desenvolver todo o ESR do projeto, como visto em [[Enterprise Service Repository (ESR)#Primeiros passos ao criar um novo projeto|Primeiros passos ao criar um novo projeto]] precisamos agora fazer a conexão entre os sistemas com o Integration Builder. Cada cenário pode ser de uma forma, portanto aqui vou abordar o cenário que eu mais utilizei, que seria **ABAP Proxy to REST API**.

1. Vamos começar desenvolvendo o objeto [[Configuration Scenario]].
2. Utilizando o nosso Configuration Scenario, precisamos agora adicionar o [[Business System]] correto e seu devido [[Communication Channel]]. Normalmente, quando o nosso cenário começa pela ABAP Proxy, já temos um Business System que aponta para o respectivo ambiente (DEV, QAS ou PRD) e também um [[Communication Channel]] criado para esse cenário. 
3. Agora, precisamos criar o nosso [[Business Component]], que representará o sistema REST. Como o nosso cenário é **ABAP Proxy to REST**, esse Business Component será configurado APENAS como "Receiver". Nele, apontamos para a operation específica da [[Service Interface]] desenvolvida no ESR (por exemplo, `SI_REST_INTEGRATION.getToken`). 
4. Ainda no [[Business Component]], na seção "Communication Channels", criamos um novo [[Communication Channel]] para o sistema REST, escolhemos o REST como 'Adapter Type' desse [[Communication Channel]], depois configuramos o método HTTP, URL, formato de dados e se for o caso, o header.
5. Agora, criamos o [[Integrated Configuration]], utilizando apenas a [[Service Interface]] e não suas operations, além do 'Communication Component' que seria o nosso [[Business System]], pois ele é o sender desse cenário (algumas vezes, o Business System também é tratado como um Business Component). Agora, precisamos configurar a ligação entre os sistemas através dos [[Business Component]], podemos definir se esse [[Integrated Configuration]] vai ser específico para cada operation da [[Service Interface]], ou se vai ser generalista. Portanto, definimos nossos [[Business Component]] aqui e podendos deixar que o PI registre todas as mensagens no log do monitor na 'Advanced Settings', dessa forma toda as mensagens do fluxo serão registradas e armazenadas para visualização no [[Monitoring]].

Normalmente, esse seria o fluxo básico para a criação de um cenário **ABAP Proxy to REST** no SAP PI. Para mais cenários ou complementações desse cenário, acesse [[Técnicas SAP PI]].

### Descrição dos objetos
Aqui está a lista de objetos do Integration Builder e suas descrições.

[[Configuration Scenario]]
[[Business Component]]
[[Business System]]
[[Communication Channel]]
[[Integrated Configuration]]