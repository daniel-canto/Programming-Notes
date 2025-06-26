#sap/sap_antigo/sap_pi/componentes_sap_pi/enterprise_service_repository/message_mapping 

```table-of-contents
```

### O que é?
Esse objeto é o processo de transformação de dados entre diferentes estruturas de mensagens, permitindo que informações enviadas por um sistema sejam convertidas no formato esperado por outro sistema.

Para isso, a SAP fornece um editor gráfico para esse objeto, onde é possível visualizar as estruturas de origem e destino e criar ligações entre seus campos, podendo ser de forma simples e direta ou aplicando funções e regras de transformação.

O mapeamento criado graficamente é convertido em [[Java]], sendo executado pelo Integration Engine do SAP PI no processamento da mensagem. Apesar disso, o Message Mapping pode ser utilizado para diferentes tipos de mensagens, como IDocs, RFCs, WSDL e XML/XSD.

---
### Uso do Message Mapping
Normalmente, importamos dentro desse objetos dois [[Message Types]] para fazer o mapeamento e apenas ligamos os campos. Isso varia de acordo com a necessidade, em alguns casos, funções do Message Mapping pode ser criadas para solucionar um problema.
![[Pasted image 20250604150859.png]]
Esse seria um exemplo de Message Mapping utilizando [[Message Types]].