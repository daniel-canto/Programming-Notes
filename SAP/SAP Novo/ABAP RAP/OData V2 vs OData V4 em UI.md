#sap/sap_novo/abap_rap/odata_v2_vs_odata_v4_em_ui 

```table-of-contents
```

### Comparativo
A principal diferença reside no fato de que o OData V4 é o padrão para o qual o ABAP RAP é otimizado, recebendo as inovações e suporte mais completo da SAP.
Abaixo, segue os detalhamentos das diferenças entre eles:

| **Característica**          | **OData V2**                                                              | **OData V4**                                                                                                   |
| --------------------------- | ------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| Padrão e recomendação       | Suportado para cenários de <br>compatibilidade e legado.                  | Padrão recomendado pela SAP para novos desenvolvimentos.                                                       |
| Funcionalidades e protocolo | Conjunto de funcionalidades mais limitado.                                | Formato JSON mais limpo e leve, reduzindo o tráfego na rede.                                                   |
| Queries                     | Ordenações de filtro `$filter` e `$orderby` básicas.                      | Linguagem de consulta mais poderosa: agregações com `$apply` e busca textual com `search`.                     |
| Suporte a draft             | Funciona, mas pode ser inconsistente.                                     | Suporte completo e otimizado para o ciclo de vida de rascunhos.                                                |
| Actions                     | Suporte básico.                                                           | Suporte a estruturas profundas (deep structures) em ações, permitindo operações complexas em um único request. |
| Anotações de UI             | Suporte maduro para Fiori Elements, mas com menos inovações.              | Recebe as últimas inovações em annotations, permitindo interfaces mais ricas e dinâmicas.                      |
| Tratamento de anexos        | Implementação pode variar.                                                | Modelo de implementação mais claro e robusto.                                                                  |
| Visibilidade dos botões     | Comportamento considerado por vezes mais previsível para ações estáticas. | A visibilidade dos botões, como o Criar, pode depender da ativação do modo Draft na BDEF.                      |
| Operações de modificações   | Utiliza o POST para a criação e MERGE para atualização parcial.           | Utiliza o PATCH padrão do HTTP para atualizações parciais, mais eficiente.                                     |

### Detalhamento das comparações
##### 1. Pode de consulta avançado com OData V4
A maior vantagem do OData V4 é sua capacidade de consulta.

- **Agregações no banco de dados (`$apply`)**: com o V4, você pode realizar agregações (soma, contagem, média) diretamente no banco de dados, que são expostas por OData. Por exemplo, podemos calcular o valor total de pedidos por cliente, usando uma única chamada, dessa forma: `$apply=groupby((customerID), aggregate(OrderAmount with sum as TotalAmount))`. No V2, seria necessário buscar todos os pedidos e fazer a agregação na lógica do ABAP ou do Frontend.

- **Busca textual (`$search`)**: o V4 traz a capacidade de busca textual em múltiplos campos de uma entidade, semelhante a um motor de busca. 

##### 2. Ações com estruturas profundas
No V4, uma ação pode receber uma estrutura complexa (uma tabela aninhada, por exemplo) como parâmetro. Isso é ideal para cenários de criação de documentos complexos, como um pedido de venda e seus itens, em uma única chamada de API. No V2, isso exigiria múltiplas chamadas em batch, tornando a lógica mais complexa.

##### 3. Comportamento em Fiori Elements
A experiência final do usuário pode variar dependendo da versão do OData.
- **Seleção múltipla**: aplicações V4 em List Report Page habilitam a seleção múltipla por padrão, enquanto na v2 era necessário configurar.
- **Visibilidade das ações**: desenvolvedores da comunidade SAP relatam que a lógica de visibilidade e habilitação de botões de ação pode ser mais direta em OData V2 para cenários simples, enquanto em V4, especialmente com draft, o framework assume mais controle, o que pode exigir um entendimento mais profundo do seu funcionamento.

### Quando considerar usar o OData V2?
Apesar do V4 possuir diversas vantagens, ainda existem cenários one o OData V2 pode ser uma escolha válida:

**1. Consumidores Legados**.
**2. Manutenção de aplicações existentes**.
**3. Simplicidade extrema**: para APIs CRUD muito simples, onde funcionalidades avançadas do V4 não são necessárias.
