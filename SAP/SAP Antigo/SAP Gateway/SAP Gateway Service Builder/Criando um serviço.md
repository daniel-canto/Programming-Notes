#sap/sap_antigo/sap_gateway/sap_gateway_service_builder/criando_um_servico

### 1 - Criando o projeto na SEGW
Para criar um serviço na transação`SEGW`, precisamos primeiro criar o projeto dentro, ao clicar no ícone de "papel em branco", normalmente apenas definimos apenas a descrição, nome e pacote atrelado.

### 2- Criar as entidades
Depois de criar o projeto, precisamos criar as entidades, para isso, vamos em `projeto_criado   -> Data Model -> Entity Types`, clicamos com o botão direto na pasta `Entity Types` e inserimos o nome da nossa entidade. Podemos deixar também ele já criar a nossa [[SAP Gateway Service Builder#EntitySet|entity set]].

##### Entidades herdades de outros objetos
Algumas entidades podem herdar características de outros objetos. Por exemplo, se queremos utilizar a `BAPIRET2` para uma entidade de log de mensagem, podemos simplesmente importar essa BAPI, clicando com o botão direito em cima do `Data Model`, depois `Import -> DDIC Structure` e depois definimos o nome que essa entidade terá e qual objeto ABAP estamos utilizando como base, que no caso seria a `BAPIRET2`. Depois, podemos selecionar quais campos desse objeto vamos utilizar.

### 3- Definir os campos
Agora, com a entidade criada, precisamos acessar sua pasta e ir em "Properties", e adicionar os campos que aquela entidade irá conter.

Caso a sua entidade seja [[Criando um serviço#Entidades herdades de outros objetos|herdada de outro objeto]], se você adicionar um novo campo criado manualmente, você deve ir na aba de `Entity Types`, procurar na listagem a sua entidade e remover o valor contido na coluna `ABAP Structure` e depois pressionar enter.

### 4- Gerar objetos
Depois de criar as entidades e seus campos, você deve simplesmente gerar os objetos. Para isso, você simplesmente irá selecionar esse ícone: ![[Pasted image 20250724094237.png]]

Normalmente, não mexemos nas informações que a próxima tela irá trazer, apenas confirmamos e inserimos no nosso pacote e request. 

### 5 - Redefinição dos métodos
Pode ser necessário redefinir nenhum, alguns ou todos os métodos de uma entidade. Para isso, vá na pasta `Service Implementation` e clique com o botão direito sobre qualquer método e selecione `Go to ABAP Workbench`.  Com isso, você será direcionado para a `se24`. 

Se você clicar na pasta `Methods`, verá todos os métodos de todas as entidades. Para redefinir elas, basta clicar com o botão direito no método desejado, depois clicar em `Redefine` e se quiser, pode apagar os comentários.

Com isso, você pode salvar e ativar.

### 6 - Implementação dos métodos
Caso necessite, você mesmo pode implementar os métodos de uma entidade. O ideal para isso, é você redefinir ele, como visto na seção anterior.