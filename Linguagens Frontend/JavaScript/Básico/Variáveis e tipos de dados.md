#frontend/javascript/basico/variaveis_e_tipos_de_dados 

```table-of-contents
```

Em primeiro lugar, o JS é uma linguagem de tipagem dinâmica.

As variáveis em JS sempre são declaradas com um var. Exemplo:

```jsx
var v1 = "Daniel"
var v2 = 'Gomes'
var v3 = `Estudando`
// As variáveis podem ser declaradas desses três jeitos, quando for uma string
```

Há algumas regras para se declarar os nomes das variáveis em JS:

- **Podem começar com letra, $ ou _**
- **Não podem começar com números**
- **É possível usar com letras e números**
- **É possível utilizar símbolos e acentos**
- **Não podem conter espaços**
- **Não podem usar palavras reservadas**
- **Em JS, as variáveis são case sensitive**
- **Use nome coerentes**

Nessa aula, foi feito um código em Node.js apenas para testar as variáveis:

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/8b6efb32-041b-4c02-ae7f-887751779fd3/4ddc6e1a-3d1e-4081-88e9-4b32bb37edf5/Untitled.png)

Para acessar o Node.js, pode usar a barra de pesquisa do Windows e abrir o Node, ou você pode abrir pelo VS Code, usando o terminal e digitando `node`.

Apesar de ser de tipagem dinâmica, o JS entende qualquer número (decimal ou não) como do tipo number.

Em JS, os principais tipos de dados são o number, string e boolean.

Porém, existem mais tipos de dados, por exemplo, o number possui duas vertentes: o infinity e o NaN (Not a Number). Além desses, há também o null, undefined, object, array (o array é uma vertente do object), e o function.

Em JS existe um comando para descobrir o tipo de dado da variável, o typeof, veja como ele funciona:

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/8b6efb32-041b-4c02-ae7f-887751779fd3/8bf137e7-a7c8-4059-baa4-778689b3646b/Untitled.png)

Por algum motivo, em JS, o tipo null é visto como uma vertente do object.