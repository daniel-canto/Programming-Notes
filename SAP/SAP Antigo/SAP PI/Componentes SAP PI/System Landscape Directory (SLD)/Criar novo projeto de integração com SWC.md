#sap/sap_antigo/sap_pi/componentes_sap_pi/system_landscape_directory/criar_novo_projeto_de_integracao_com_swc

Quando vamos desenvolver um novo projeto de integração no SAP PI, antes precisamos criar uma SWC para a integração.

Portanto, para isso vamos no SLD e vamos seguir o passo a passo abaixo.

##### Passo a passo

1. Primeiro, precisamos criar o nosso produto. Para isso, dentro do SLD na categoria **Software Catalog**, clicamos em '**Products**'.

2. Nessa tela, podemos ver todos os produtos disponíveis no sistema. Nessa tela clicamos em **'New**'. A próxima tela, pergunta se queremos criar uma nova versão para um produto existente ou se queremos criar um novo produto e versão, no caso selecionamos a segunda versão, pois estamos começando um novo projeto agora.

3. Agora, haverá uma tela com 3 campos de texto. Cada um deve ser preenchido da seguinte forma:
   **Product Name**: define o nome do produto. Não é obrigatório, mas pode ser uma boa prática ter um prefixo Z. Exemplo: `Z_TEST_INTEGRATION`.
   **Product Vendor**: o padrão pode variar para cada projeto/cliente, mas normalmente aqui eu coloco a empresa desenvolvedora da integração que eu estou trabalhando.
   **Product Version**: definimos a versão do produto, por ser o início de um novo projeto, podemos colocar `1.0` nesse campo.

4. Agora, clicamos em **'Next'** e agora ele vai pedir pelo **Instance Name**, normalmente eu faço dessa forma: `{nome_produto}_{nome_ambiente}`, por exemplo: `Z_TEST_INTEGRATION_DEV`.

5. Agora é so criamos o SWC. Para isso, precisamos preencher 2 campos:
   **Name**: nome da SWC, normalmente coloco igual ao nome do produto, por exemplo: `Z_TEST_INTEGRATION`.
   **Version**: assim como na versão de componente, colocamos `1.0`.
   O campo **Production Site** pode ficar como "released" mesmo.

Com esses 5 passos, você já deve ter conseguido criar o seu SWC. Agora, o próximo passo para o desenvolvimento seria aprender a utilizar o [[Enterprise Service Repository (ESR)]], para o desenvolvimento das estruturas e mapeamentos de campos.