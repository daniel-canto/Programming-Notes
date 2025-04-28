 #frontend/javascript/frameworks/reactjs/jsx_em_react   

```table-of-contents
```

Como já sabemos, o JSX é utilizado para trabalhar com HTML dentro do JavaScript. 
Apesar disso, há alguns diferenças do HTML padrão, que vou ir mencionando abaixo.


### Regras de uso do JSX
* ~={green}~={orange}**Self-closing tags devem ser fechadas.**=~=~ Tags como `<img>`  devem ser fechadas em React dessa forma: `<img/>`
* Na função que retorna o HTML da página, ~={orange}**é~={orange} =~obrigatório colocar os elementos dentro de uma tag pai**=~=~, como uma `<div>`.
* Em HTML padrão, utilizamos a sintaxe `class=` para uma tag. Entretanto, em React, `class` é uma palavra reservada. ~={green}~={orange}Para criar classes HTML, precisamos fazer utilizando o =~`className=`=~. Caso contrário, um erro será retornado.


### Técnicas de uso do JSX
* **Interpolação de variáveis JS**. Podemos usar os valores das variáveis dentro do HTML, utilizando `{nome}`. 