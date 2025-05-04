#frontend/javascript/frameworks/reactjs/react_fragments

```table-of-contents
```

### O que é?
~={green}O React Fragments permite a criação de um componente sem precisar de um elemento pai no retorno, ou seja, uma `<div>`=~. Ao invés disso, podemos simplesmente usar um fragment para manter o HTML gerado mais limpo.

Portanto, ele não gera elementos extras no DOM, pois ao contrário de uma `<div>`, o fragment não aparece na estrutura final do HTML. Com isso, ele ajuda a evitar estruturas HTML inválidas, como uma `<div>` dentro de uma `<tr>`.

----
### Como utilizar?
Podemos usar de duas formas, que vou listar abaixo:

##### Sintaxe completa
Seria escrito dessa forma: `<React.Fragment>...</React.Fragment>`.
~={green}Para utilizar uma propriedade `key` =~(como renderizar uma lista), você deve utilizar essa sintaxe: `<React.Fragment key={alguma_copisa}>...</React.Fragment>`.

##### Sintaxe abreviada
Seria escrito dessa forma: `<>...</>`.
~={orange}Entretanto, se você deseja utilizar uma propriedade `key` (como renderizar uma lista), você deve utilizar a sintaxe completa=~, pois a forma abreviada não aceita atributos.

##### Exemplo
```jsx
function MeuComponente() {
  return (
    <>
      <h1>Título</h1>
      <p>Parágrafo</p>
    </>
  );
}
```
