#sap/sap_antigo/sap_pi/tecnicas_sap_pi/como_gerar_estrutura_da_proxy_no_abap 

```table-of-contents
```

### SPROXY
Para gerar as estruturas da sua integração em forma de proxy, você deve acessar a transação `SPROXY`. Dentro dessa transação, você tem a seguinte tela inicial:
![[Pasted image 20251107111436.png]]

Nessa tela, nas pasta à esquerda você deve percorrer  seguinte caminho: `Source/ESR/SWCs` e encontrar e dar dois cliques na SWC da sua integração.

Agora, você vai acessar a pasta `Namespaces`, entrar no namespace da sua integração. Aqui, você tem como exibir os objetos por tipo, no caso para gerar, eu sempre puxo todos os objetos do namespace, clicando em `Objects`.

Agora, eu sempre gero as proxys das estruturas dos objetos do tipo SI. Portanto, vou em cada um deles e vou gerando, primeiro o Outbound e depois o Inbound. Para gerar, clique com o botão direito no objeto e selecione `Generate`.

Com isso, o objeto será gerado. Agora, aperte no ícone de salvar na parte superior da tela e repita o processo para todos os outros SIs. Com isso, além dos SIs, as estruturas relacionadas devem estar geradas também, o último passo agora é ativar.

Com isso, sua integração já deve estar pronta para uso.

> [!NOTE] Pontos de atenção!
> Se for um cenário Proxy to SOAP por exemplo, por conta do [[External Definition]], pode ocorrer que a SI de inbound seja gerada corretamente e ativada, mas fique com um ícone como se não tivesse (um círculo branco e vermelho). Se ao clicar duas vezes ele mostrar a classe gerada e afins, está tudo certo. Vale ressaltar que a SI de Inbound nem será utilizada por um programa ABAP, então ela também não deve impactar. Pois a SI Inbound representa o sistema de destino.

