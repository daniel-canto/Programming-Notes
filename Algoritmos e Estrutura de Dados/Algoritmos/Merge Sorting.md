#algoritmos_e_estrutura_de_dados/algoritmos/merge_sorting 

```table-of-contents
```

### O que é?
O Merge Sorting é um algoritmo de ordenação eficiente baseado na estratégia de dividir e conquistar. Ele resolve o problema de ordenar uma lista dividindo-a repetidamente em partes menores, ordenando essas partes e, finalmente, mesclando-as de volta em uma lista ordenada.

----
### Etapas do Merge Sort
**1. Dividir**
O array original é dividido [[Recursividade|recursivamente]] ao meio até que cada sublista tenha apenas um elemento (ou esteja vazia). Uma lista com apenas um elemento já está ordenada, pois não há nenhum outro elemento para ser maior ou menor.

**2. Conquistar (Ordenar)**
Cada sublista é ordenada recursivamente. Como cada sublista tem apenas um elemento, não é necessário ordená-la explicitamente.

**3. Mesclar (Merge)**
Duas sublistas ordenadas são combinadas em uma nova lista também ordenada. Esse processo é chamado de "intercalação" ou "fusão". A cada etapa, compara-se o menor elemento de cada sublista e o menor é adicionado à lista final, repetindo até que todos os elementos sejam processados.

---
### Exemplo conceitual

    