#algoritmos_e_estrutura_de_dados/estrutura_de_dados/struct 

```table-of-contents
```
### O que é?
É uma estrutura de dados composta que permite agrupar diferentes variáveis, geralmente de tipos distintos, sob um mesmo nome. Assim, você pode criar um novo tipo de dado que representa um conjunto lógico de informações relacionadas, como os dados de um aluno, um livro ou um paciente.
Vale ressaltar, que uma struct pode conter outra struct.
Normalmente, essa estrutura é muito associada à [[C|linguagem C]], porém ela esta presente em [[C++]], [[C#]], [[Go]] e [[Rust]].  

### Exemplo em C
```c
#include <cs50.h>
#include <stdio.h>
#include <string.h>

typedef struct {
  string name;
  string number;
}
person;

int main(void) {

  person people[3];

  people[0].name = "David";
  people[0].number = "+1-617-495-1000";
}
```
