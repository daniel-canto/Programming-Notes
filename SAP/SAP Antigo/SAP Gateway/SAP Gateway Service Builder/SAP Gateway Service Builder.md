#sap/sap_antigo/sap_gateway/sap_gateway_service_builder 
#topico_nv3 

### O que é?
É uma ferramenta do SAP Gateway utilizada para criar ou modificar o projeto do seu serviço OData. Essa ferramenta pode ser acessada pela transação `SEGW`.

---
### Objetos e conceitos
##### Entity
É uma estrutura de dados disponível no serviço. Você pode criar quantas entidades precisar, como Cliente, Pedido, Venda, Item e etc.
![[Pasted image 20250723101038.png]]

##### EntitySet
Ele é uma coleção de entidades (entity) no serviço. Na sua configuração, você pode habilitar ou desabilitar alguns recursos, como: criação, atualização, exclusão e etc.
![[Pasted image 20250723101410.png]]

##### Associação
É o relacionamento entre entidades no serviço. Na imagem abaixo, temos a entidade de cabeçalho (ZSOHEADER) e a entidade de item (ZSOITEM), nesse caso, um cabeçalho pode ter 0 ou mais itens, dessa forma você consegue acessar os itens de uma ordem usando o protocolo OData.
![[Pasted image 20250723101731.png]]

##### Function Import 
É uma função que pode ser chamada no serviço, podendo ter parâmetros de entrada e saída.
![[Pasted image 20250723101944.png]]

##### Service Implementation
É onde você define a implementação da lógica para cada operação do REST para as entidades do serviço.
![[Pasted image 20250723102221.png]]

##### Runtime Artifacts
Aqui, é contido os objetos como classes, serviços e modelos registrados.
![[Pasted image 20250723102514.png]]

##### Classes do serviço
Dentro do Runtime Artifacts, temos alguns tipos de classes.
* Classe MPC: contém os campos das entidades.
* Classe DPC: contém os métodos das entidades.
* MDL: modelo registrado.
- SRV: serviço registrado.

**Atenção:** Apenas as classes com final `_EXT` podem ser modificadas, as outras classes são geradas pela SEGW.

##### Service Maintenance
Ele representa o serviço do seu projeto, mostrando seu status e acesso a outras transações relacionadas como registro, manutenção, log de erros e [[SAP Gateway Client]].

---
### Criando um serviço
[[Criando um serviço]]