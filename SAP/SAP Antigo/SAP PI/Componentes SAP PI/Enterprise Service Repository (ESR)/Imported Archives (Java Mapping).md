#sap/sap_antigo/sap_pi/componentes_sap_pi/system_landscape_directory/imported_archives 

```table-of-contents
```

### O que é?
Popularmente conhecido como Java Mapping, é um objeto do [[Enterprise Service Repository (ESR)]] que permite importar e utilizar códigos [[Java]] customizados para transformação de mensagens em cenários de integração.

Portanto, ele é basicamente um repositório de arquivos compactados (.JAR) que contêm classes [[Java]] desenvolvidos pelo usuário para realizar mapeamentos de mensagem. Esses arquivos são importados para o ESR e ficam disponíveis para serem utilizados em [[Operation Mapping]], permitindo transformar, enriquecer ou manipular mensagens de forma avançada e personalizada.

---
### Características
**Mapeamento avançado:** usado quando as regras de transformação são complexas demais para o mapeamento gráfico padrão ou quando é necessário manipular a mensagem de forma programática.

**Reutilização:** o mesmo arquivo pode ser utilizado em diferentes [[Operation Mapping]] e cenários de integração.

**Flexibilidade:** permite implementar lógicas que não são possíveis via mapeamento gráfico com [[Message Mapping]], como manipulação de estruturas XML complexas, chamadas externas, validações específicas, entre outros.

---
### Como funciona
1. **Desenvolvimento:** O desenvolvedor cria uma classe Java que implementa a interface `StreamTransformation` (ou herda de `AbstractTransformation`) da API de mapeamento do SAP PI. É necessário importar a biblioteca `aii_map_api.jar` para acessar essa API.
	
2. **Empacotamento:** O código Java é compilado e empacotado em um arquivo .JAR.
	
3. **Importação:** No ESR, o arquivo .JAR é importado como um objeto do tipo Imported Archives
	
4. **Associação:** O Java Mapping é associado a um Operation Mapping, onde será chamado durante o processamento da mensagem.
    
5. **Execução:** Quando o cenário de integração é executado, o SAP PI utiliza o código Java do Imported Archives para transformar a mensagem conforme a lógica implementada.

Para saber como **desenvolver classes de Java Mapping**, veja a seção abaixo.

----
### Como desenvolver um Java Mapping

##### Passo 1 - Configurar ambiente de desenvolvimento
Para desenvolver um Java Mapping, antes precisamos baixar o Eclipse NetWeaver Developer Studio. Ele serve para muitas coisas envolvendo o SAP On-Premise, e principalmente, criações de Java Mapping para o SAP PI.

Portanto, já deixei um Eclipse pronto para uso: https://drive.google.com/file/d/1Xu983CyxLShINc_ikZG4Y3oI8ldlNs5u/view?usp=drive_link.

Depois que o Eclise estiver pronto para uso, precisamos baixar esse JDK específico, que suporta o NWDS:  https://drive.google.com/file/d/1or__yxblS4RB7Knfdj7-YSr-E2BGx3NK/view?usp=drive_link

##### Passo 2: Criar um projeto Java
Dentro do Eclipse NWDS, agora vamos criar um novo projeto, portanto seguimos o passo a passo abaixo.

1. No Eclipse, clicamos na aba 'File' -> 'New' -> 'Java Project'. Nessa primeira tela, podemos definir um nome para o projeto no geral, que pode conter um ou mais mappings. Após definir o nome, na seção JRE, selecione a opção "Use default JRE (currently 'jre1.8.0_431)')". Esse JRE é o que instalamos no passo 1. Depois clique em 'Next'.
	
2. Na próxima tela, vamos na aba 'Libraries' e clicamos no botão 'Add Library', dentre as seleções que aparecem, selecione a 'XPI Library' e depois 'Finish' e depois 'Finish' de novo.
	
3. Agora, na pasta 'src' do projeto, clique com o botão direito sobre ela, depois 'New' -> 'Package'. Definimos o nome do pacote como "com.map".
	
4. Agora, vamos criar a classe que irá conter o código do nosso Java Mapping. Para isso, clique com o botão direito sobre o pacote recém criado e clicamos em 'New' -> 'Class'. O nome da classe deve seguir a boa prática padrão: sem espaços e com todas as letras iniciais de cada palavra maiúsculas.
	
5. Agora, implemente a classe criada com a lógica necessária.

##### Passo 3 - Importar Java Mapping no SAP PI
1. Para importar no SAP PI, clique na classe com o botão direito, vá para 'Export...' -> 'JAR file', selecione o destino em que deseja salvar e depois 'Finish'.
	
2. Por fim, crie um objeto "Imported Archive" no SAP PI, selecione o JDK 1.8 (só é suportado em PI com NetWeaver versão 5 ou superior) e importe o JAR exportado anteriormente.
	
3. Pro mapeamento ser executado, você deve ir ao seu [[Operation Mapping]], na interface de envio desejada (outbound ou inbound, por exemplo), selecionar 'Java Mapping' e depois colocar o Imported Archives criado. Dessa forma, seu mapeamento já está pronto para uso.

---
### Java Mappings desenvolvidos
Eu possuo um repositório com alguns Java Mappings desenvolvidos, que estão com o seu funcionamento documentado e também já foram testados e utilizados.
Eles estão localizados aqui: [daniel-canto/sap-pi-utils](https://github.com/daniel-canto/sap-pi-utils)

Normalmente, eles são utilizados em casos específicos, onde são encontradas individualidades que precisam ser contornadas, pois apenas os objetos comuns não são capazes de resolver. Portanto, acesse [[Técnicas SAP PI]] para uma documentação completa dessas soluções.