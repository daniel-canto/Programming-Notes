#algoritmos_e_estrutura_de_dados/algoritmos/linear_search 

```table-of-contents
```

### O que é?
A Linear Search é um algoritmo simples usado para encontrar um elemento específico em uma lista ou array. Ele funciona verificando cada elemento sequencialmente, do início ao fim, até encontrar o valor desejado ou concluir que ele não está presente.

----
### Funcionamento
O algoritmo inicia no primeiro elemento da lista e compara-o com o valor salvo. Se houver correspondência, retorna a posição do elemento. Caso contrário, avança para o próximo item, repetindo o processo até percorrer todo o array. Por exemplo, em um array `[5, 3, 7, 2]`, buscar o número 7 exigiria verificar os elementos nas posições 0, 1 e 2, respectivamente 5, 3 e 7.

----
### Vantagens
- **Simplicidade**: fácil de implementar, ideal para iniciantes.
- **Versatilidade**: funciona em listas não ordenadas e em diferentes estruturas de dados, como arrays e [[Lista Encadeada|listas encadeadas]].
- **Sem pré-requisitos**: não exige que os dados estejam organizados previamente.

### Desvantagens
- **Ineficiente em grandes conjuntos**: sua complexidade de tempo é `O(n)` no pior caso (onde `n` é o número de elementos), tornando-o lento para listas extensas.
- **Comparação com algoritmos eficientes**: em listas ordenadas, o algoritmo [[Binary Search]] (complexidade `O(log n)`) é significativamente mais rápida.

----
### Exemplo em C
Aqui está um exemplo básico de Linear Search em [[C]]:
```c
// Função de busca linear
int buscaLinear(int a[], int tamanho, int chave) {
  for (int i = 0; i < tamanho; i++) {
    if (a[i] == chave) {
      return i; // Retorna o índice se encontrar
    }
  }
  return -1; // Retorna -1 se não encontrar
}
```

Como podemos ver, é o tipo mais comum de algoritmo de pesquisa.