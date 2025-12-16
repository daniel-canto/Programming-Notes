#sap/sap_antigo/sap_pi/tecnicas_sap_pi/cenario_abap_proxy_to_soap 

```table-of-contents
```

Aqui, vou listar a forma como devemos criar uma integração com ese cenário.

Por ser Proxy como Outbound, seguimos praticamente o mesmo fluxo do [[Criando um cenário ABAP Proxy to REST]]. Portanto, é mais fácil eu listar as diferenças do que explicar a mesma coisa novamente.

~={orange}Vale ressaltar que é de suma importância termos o WSDL da API que será integrada=~, pois sem esse documento não conseguimos desenvolver esse cenário corretamente.

### Etapa 1: ESR
Temos uma pequena diferença no ESR quando o Receiver é um SOAP, por conta do payload do SOAP que requere o envelopamento e também o namespace da API nos campos da requisição. Com certeza podemos fazer isso utilizando um [[Imported Archives (Java Mapping)]], usando código, mas não é o ideal.

Portanto, vamos ao desenvolvimento.

Antes de começarmos, você pode e deve desenvolver as estruturas de Outbound e Inbound normalmente, assim como no [[Criando um cenário ABAP Proxy to REST|cenário REST]]. No entanto, após desenvolver os [[Data Types]] e [[Message Types]], você deve criar o objeto [[External Definition]].

