#algoritmos_e_estrutura_de_dados/algoritmos/recursividade 

```table-of-contents
```
### O que é?
É caracterizado por uma função, procedimento ou rotina que faz referência a si mesma durante sua execução. É quando uma função chama a si mesma para resolver um problema, geralmente dividindo-o em subproblemas menores do mesmo tipo até atingir um caso simples, chamado de **caso base**.

### Exemplo em C
Aqui está o exemplo explicado de recursividade usando a [[C|linguagem C]]. 

O código abaixo tem como objetivo escrever uma pirâmide de forma dinâmica, com base na altura que o usuário escolhe utilizando recursividade.
```c
#include <cs50.h>
#include <stdio.h>

void draw(int n);

int main(void) {
  int height = get_int("Height: ");
  draw(height);
}

void draw(int n) {
  if (n <= 0) {
    return;
  }

  draw(n - 1);

  for (int i = 0; i < n; i++) {
    printf("#");
  }
  printf("\n");

}
```
1. **Caso base:**  
    O código começa testando `if (n <= 0) return;`. Isso impede que a função continue chamando a si mesma indefinidamente. Quando `n` chega a 0, a função simplesmente retorna, encerrando a recursão naquele "ramo".
    
2. **Chamada recursiva:**  
    Antes de imprimir qualquer coisa, a função chama `draw(n - 1);`. Isso significa que, para cada valor de `n`, ela primeiro resolve o problema para um valor menor (`n-1`), empilhando chamadas na memória (call stack).
    
3. **Impressão após a recursão:**  
    Só depois que a chamada recursiva retorna, o laço `for (int i = 0; i < n; i++) printf("#");` é executado, imprimindo uma linha com `n` blocos.
    
##### Ordem de execução do código
A recursão faz com que as linhas sejam impressas de cima para baixo (do menor para o maior):
- Suponha que o usuário digite `3`.
- O fluxo será:
    - `draw(3)` chama `draw(2)`
        - `draw(2)` chama `draw(1)`
            - `draw(1)` chama `draw(0)` (caso base, retorna)
            - imprime 1 bloco: `#`
        - imprime 2 blocos: `##`
    - imprime 3 blocos: `###`
        
Ou seja, **primeiro as chamadas recursivas descem até o caso base, depois, conforme cada chamada retorna, imprime a linha correspondente**. Isso garante que a primeira linha impressa tenha 1 bloco, a segunda 2, e assim por diante, formando a pirâmide correta.

##### Por que funciona assim?
- **A função "lembra" onde parou:**  
    Cada chamada de `draw(n)` só imprime sua linha depois que `draw(n-1)` termina. Assim, a impressão ocorre na ordem crescente de linhas, de 1 até `n`.
- **Recursão como empilhamento:**  
    Pense na recursão como uma pilha (stack): primeiro empilha todas as chamadas até o caso base, depois vai "desempilhando", imprimindo de baixo para cima (menor para maior).
