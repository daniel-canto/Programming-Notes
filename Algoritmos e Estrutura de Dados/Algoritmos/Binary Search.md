#algoritmos_e_estrutura_de_dados/algoritmos/binary_search 

```table-of-contents
```

### O que é?
É um algoritmo eficiente para encontrar um elemento em uma lista ordenada. Seu funcionamento é baseado no paradigma de "dividir e conquistar": a cada passo, o algoritmo compara o elemento do meio da lista com o valor procurado e, dependendo do resultado, descarta metade dos elementos, reduzindo drasticamente o número de comparações necessárias.

----
### Funcionamento
1. O algoritmo começa definindo dois índices: inicio e fim da lista.
2. Calcula o índice do elemento do meio.
3. Compara o valor do meio com o valor procurado:
	1. Se for igual, a busca termina com sucesso.
	2. Se o valor do meio for maior, a busca continua apenas na metade inferior da lista.
	3. Se o valor do meio for menor, a busca continua apenas na metade superior.
4. Repete o processo até encontrar o elemento ou até que o intervalo de busca seja vazio.

----
### Exemplo conceitual
Por exemplo, imagine uma lista ordenada `[1, 3, 5, 7, 9, 11, 13, 15]`e agora precisamos buscar o número 9.
Para isso, seguimos esses passos:
1. O algoritmo começa definindo os limites inicial (`inicio = 0`) e (`final = 7`) da lista (pois a lista contém 8 possibilidades, com sua contagem de índices começando em 0), correspondentes aos índices do primeiro e último elemento. O objetivo é reduzir progressivamente o intervalo de busca até encontrar o elemento desejado ou concluir que ele não está presente. Portanto, criamos esses parâmetros iniciais:
       Parâmetros Iniciais:
	- **Lista**: `[1, 3, 5, 7, 9, 11, 13, 15]`
	- **Valor buscado**: `9`
	- **Índices**: `inicio = 0`, `fim = 7`

2. **Primeira Iteração: comparação com o elemento do meio**
       O algoritmo calcula o índice do elemento central:
       $$ meio =  \frac{inicio + fim}{2} = \frac{0 + 7}{2} = 3$$
	 O elemento no índice `[3]` é o elemento `7`. Como `7 < 9` , o algoritmo descarta a       metade inferior da lista (elementos menores ou iguais a 7) e atualizar o limite inferior:
	 $$inicio = meio + 1 = 4$$
	
	O estado atual do array seria:
	- Intervalo de busca: `[9, 11, 13, 15]` (índice 4 a 7.)

3. **Segunda iteração: Redefinição do Intervalo**
       O novo elemento central é calculado:
       $$meio = \frac{4 + 7}{2} = 5$$
       O elemento no índice `[5]`é o elemento `11`. Como `11 < 9`, o algoritmo descarta a metade superior da lista (elementos maiores ou iguais a 11) e atualiza o limite superior.
       $$fim = meio - 1 = 4$$
       O estado atual do array seria:
       - Intervalo de busca: `[9]`  (índice `[4]`)

4. **Terceira iteração: Encontro do Elemento**:
	Com $inicio = 4$ e $fim = 4$, o elemento central é: $$meio = \frac{4 + 4}{2} = 4$$
	O elemento no índice `[4]` é o elemento 9, que corresponde ao valor buscado. O algoritmo retorna o índice 4, indicando a posição do elemento na lista.