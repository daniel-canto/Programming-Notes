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
1. **Desenvolvimento:** O desenvolvedor cria uma classe Java que implementa a interface `StreamTransformation` (ou herda de `AbstractTransformation`) da API de mapeamento do SAP PI. É necessário importar a biblioteca `aii_map_api.jar` para acessar essa API[](https://learntips.net/implementing-a-java-mapping-in-sap-pi/
2. **Empacotamento:** O código Java é compilado e empacotado em um arquivo .JAR.
	
3. **Importação:** No ESR, o arquivo .JAR é importado como um objeto do tipo Imported Archives[](https://help.sap.com/doc/saphelp_ewm900/9.0/en-US/f8/91a732526144658a08b2c8186921a1/content.htm)[](https://www.scribd.com/doc/136424381/SAP-PI-7-11-Java-Mapping-Step-by-Step)[](https://learntips.net/implementing-a-java-mapping-in-sap-pi/).
	
4. **Associação:** O Java Mapping é associado a um Operation Mapping, onde será chamado durante o processamento da mensagem[](https://www.scribd.com/doc/136424381/SAP-PI-7-11-Java-Mapping-Step-by-Step)[](https://community.sap.com/t5/technology-blogs-by-members/multimapping-in-sap-pi-graphical-java-simple-dom-sax-xslt-abap-for-dummies/ba-p/13133028)[](https://learntips.net/implementing-a-java-mapping-in-sap-pi/).
    
5. **Execução:** Quando o cenário de integração é executado, o SAP PI utiliza o código Java do Imported Archives para transformar a mensagem conforme a lógica implementada.

Para saber como **desenvolver classes de Java Mapping**, veja a seção abaixo.

----
### Como desenvolver um Java Mapping
