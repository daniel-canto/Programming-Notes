#sap/sap_novo/sap_btp/abap_environment 

```table-of-contents
```

### O que é?
O ABAP Environment é uma oferta de plataforma como serviços (PaaS) dentro do BTP que permite aos desenvolvedores criar, executar e gerenciar aplicações ABAP na nuvem SAP.
Ele foi projetado para ser o pilar do modelo de[[Extensibilidades#Extensibilidade Side-by-Side| extensibilidade Side-by-Side]] para desenvolvedores que já possuem conhecimento e experiência com ABAP.
Esse serviço é implementado no [[Cloud Foundry]] da sua subaccount.

##### Cenário 1: BTP ABAP Environment com SAP S/4 Hana Cloud
![[Pasted image 20250903114126.png]]

##### Cenário 2: BTP ABAP Environment com SAP S/4 Hana On-Premise
![[Pasted image 20250903114311.png]]
Diferentemente do cenário 1, como podemos ver, no On-Premise precisamos configurar a conexão entre o SAP BTP e o [[SAP S/4 HANA]] através do [[Cloud Connector]].

Há uma outra forma de se obter o ABAP Environment sem necessitar do SAP BTP para utilizar esse serviço, pois o [[SAP S/4 HANA Cloud]] oferece uma capacidade de [[Extensibilidades#Extensibilidade In-App|extensibilidade In-App]] chamada [[Extensibilidades#Tipos de extensões|Developer Extensibility]], que utiliza o mesmo modelo de desenvolvimento do ABAP Cloud, entretanto esse ambiente irá rodar na mesma stack do S/4 HANA Cloud.
Essa oferta surgiu para permitir extensões In-App que mantêm o core limpo.

### Comparação entre S/4 HANA ABAP Environment e BTP ABAP Environment

|  **Característica**  | **SAP BTP ABAP Environment (Steampunk)**                               | **S/4HANA Cloud Developer Extensibility (Embedded Steampunk)**                                 |
| :------------------: | :--------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------- |
|      Onde Roda?      | Na plataforma SAP BTP.                                                 | Dentro da pilha do SAP S/4HANA Cloud.                                                          |
|   Tipo de Extensão   | Side-by-Side (Lado a Lado).                                            | In-App (Na Aplicação).                                                                         |
|     Acoplamento      | Fracamente acoplado (comunica-se com o S/4HANA via APIs de rede).      | Fortemente acoplado (roda na mesma transação lógica do S/4HANA).                               |
| Finalidade Principal | Criar novas aplicações, integrações complexas, processos desacoplados. | Adicionar campos, validações e lógicas de negócio diretamente nos processos padrão do S/4HANA. |
|    Necessita BTP?    | Sim, é um serviço do BTP.                                              | Não, é uma capacidade nativa do S/4HANA Cloud.                                                 |

---
### ABAP Cloud
A principal mudança introduzida não é apenas a localização do ambiente (nuvem vs on-premise), mas sim o modelo de desenvolvimento. Para garantir estabilidade, segurança e atualizações contínuas, o ABAP Environment impõe um novo conjunto de regras chamado "ABAP Cloud Development Model".

##### Características
- **Uso exclusivo de APIs públicas**: os desenvolvedores não podem acessar diretamente as tabelas dos banco de dados ou chamar funções de um sistema back-end de qualquer maneira. A comunicação deve ser feita exclusivamente através de APIs estáveis e liberadas pela SAP (APIs REST/OData, CDS View etc). Isso garante que, mesmo que a SAP mude a estrutura interna do S/4 HANA em uma atualização, a sua extensão continuará funcionando porque a assinatura da API permanece a mesma.

- **Linguagem ABAP otimizada para a nuvem**: o ambiente utiliza uma versão moderna do ABAP. Comandos antigos e obsoletos, ou aqueles que podem causar instabilidade (como manipulação direta do sistema de arquivos do servidor) são proibidos.

* **Extensibilidade restrita**: o código desenvolvido no ABAP Environment roda em um "container" isolado. Assim, ele não interfere em outras soluções.

* **Apenas o Eclipse ADT pode ser usado como ambiente de desenvolvimento**.
