#algoritmos_e_estrutura_de_dados/algoritmos/selection_sorting

```table-of-contents
```

### O que é?
É um algoritmo de ordenação simples utilizado para organizar elementos em um array ou lista. Seu funcionamento consiste em, repetidamente, encontrar o menor elemento da parte não ordenada da lista e colocá-lo na posição correta, trocando com o elemento da posição atual.
Portanto, apesar de sua simplicidade, ele é um dos algoritmos de ordenação menos eficiente existente.

----
### Exemplo conceitual
Temos a lista: {7, 2, 5, 4, 1, 6, 0, 3}.

Começamos a verificação da esquerda para a direita, portanto o 7 é o elemento da posição atual.
Comparamos ele com todo o restante do array, até identificarmos o menor dos números menor que 7, nesse caso seria o 0. Com isso, colocamos o 0 no lugar do 7 e vice-versa, assim o array ficaria assim:
{0, 2, 5, 4, 1, 6, 7, 3}
Agora, iriamos para o próximo índice, que estaria o elemento 2.
E assim seria repetidamente, até que todo o array estivesse ordenado de forma crescente.
