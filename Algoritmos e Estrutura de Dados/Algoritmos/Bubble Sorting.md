#algoritmos_e_estrutura_de_dados/algoritmos/bubble_sorting 

```table-of-contents
```

### O que é?
É um algoritmo de ordenação simples, onde ele organiza uma lista de elementos comparando repetidamente pares de elementos adjacentes e trocando-os de posição caso estejam na ordem errada. O nome bolha se deve ao fato de que, a cada passagem, o maior elemento "flutua" para o final da lista, como uma bolha sobe à superfície da água.

---
### Exemplo conceitual
Dado o vetor `[5][3][4][1][2]`:
1. Compare 5 e 3 → troca (3, 5, 4, 1, 2)
2. Compare 5 e 4 → troca (3, 4, 5, 1, 2)
3. Compare 5 e 1 → troca (3, 4, 1, 5, 2)
4. Compare 5 e 2 → troca (3, 4, 1, 2, 5)
    
No final da primeira passagem, o 5 já está na última posição. O processo se repete para os demais elementos.
Abaixo, segue um pseudo-code desse algoritmo:
```pseudocode
Repeat n-1 times // tamanho do array
	For i from 0 to n-2
		If numbers[i] and numbers[i+1] out of order
			Swap them
	If no swaps
		Quit
```

Deve-se tomar cuidado no entanto com o final do array, pois você deve fazer a iteração utilizando algo como `For i from 0 to n-2`. O `n-2` garante que você vai analisar apenas os elementos sem nenhum problema, pois o último elemento não possuí um índice a sua frente para analisar, tendo um problema de lógica no `numbers[i+1]`.

Além disso, o algoritmo Bubble Sort pode ser otimizado para interromper precocemente se nenhuma troca ocorrer em uma passagem completa pelo array. Isso ocorre porque a ausência de trocas em qualquer iteração (incluindo a primeira) indica que todos os elementos adjacentes já estão na ordem correta, o que implica que toda a lista está ordenada.
Isso ocorre pois se nenhum swap é necessário durante uma passagem completa, significa que para todo índice `i` no array, `elemento[i] <= elemento[i+1]`.
Logo, essa condição é a definição matemática de uma lista **totalmente ordenada**.