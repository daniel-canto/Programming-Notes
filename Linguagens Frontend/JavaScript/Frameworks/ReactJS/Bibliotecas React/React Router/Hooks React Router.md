#frontend/javascript/frameworks/reactjs/bibliotecas_react/react_router/hooks_react_router 

```table-of-contents
title: 
style: nestedList # TOC style (nestedList|nestedOrderedList|inlineFirstLevel)
minLevel: 0 # Include headings from the specified level
maxLevel: 0 # Include headings up to the specified level
includeLinks: true # Make headings clickable
hideWhenEmpty: false # Hide TOC if no headings are found
debugInConsole: false # Print debug info in Obsidian console
```


Sua definição é a mesma para os [[Hooks|hooks]] padrão do ReactJS. Entretanto, a biblioteca React Router possuí os seus próprios hooks.

##### useNavigate
É um hook que permite navegar programaticamente entre rotas dentro de componentes. Basicamente, ele serve para redirecionamento. 
**Exemplo:** quando você realiza um login e é automaticamente direcionado para a página principal do site.

Portanto, com esse hook podemos ir para outras views, entretanto, podemos também passar variáveis. Muito útil para criamos redirecionamento com mensagens, como "Bem vindo, {nome}".
**Exemplo em código: 
```jsx
import { useNavigate } from "react-router-dom";

function MeuComponente() {
  const navigate = useNavigate();

  function handleClick() {
    const state = { message: `Bem vindo, ${nome}` };
	navigate("/welcome", {state}); //redireciona para a view Welcome passando uma mensagem
  }

  return <button onClick={handleClick}>Ir para Dashboard</button>;
}

```
Com isso, estamos passando uma informação junto ao redirecionamento do usuário.

##### useLocation
Permite acessar o objeto de localização atual da aplicação, ou seja, informações sobre a URL atual, incluindo o caminho (`pathname`), parâmetros de busca (`search`), hash e estado de navegação.
Portanto, ele é útil para:
    - Saber em qual rota o usuário está.
    - Ler parâmetros da URL.
    - Condicionar a renderização de componentes com base na rota.
    - Acessar dados passados via estado de navegação, ou seja, coletando a informação passada pelo [[Hooks React Router#useNavigate|useNavigate]].
Aqui, está o exemplo de `useLocation`, em conjunto com o exemplo acima do `useNavigate`:
```jsx
import { useLocation } from "react-router-dom"

const location = useLocation()

let message = ''

if(location.state) {
	message = location.state.message
}
```
