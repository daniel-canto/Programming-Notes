 #frontend/javascript/frameworks/reactjs/arquivos_base_do_react   

```table-of-contents
```

Ao gerar um novo projeto em React, uma estrutura de pastas é gerado. Aqui, explicarei as funções delas.

###### /public/index.html 
Esse arquivo serve como ponto de partida, esse é o arquivo que o navegador irá carregar. Como citado em outras anotações, o React possuí a renderização ~={blue}SPA.=~
No caso, o React vai trabalhar dentro desse arquivo, mais especificamente na `div` que contém o `id="root"`, o React **renderiza toda a aplicação dentro dessa div**.

###### ./src/index.js 
Ele vai importar o componente app (`app.js`) e vai inserir na nossa `div` com `id="root`, presente no `index.html`, usando o ReactDOM.

###### .src/index.css 
Ele contém o CSS global da aplicação, ou seja, **estiliza toda a aplicação**.

###### ./src/app.js: 
Esse é o **componente raiz** da aplicação React. Ele mostra o conteúdo principal e pode importar outros componentes. Por ser ele quem mostra os componentes, é aqui que fazemos o uso de [[JSX]], como visto em [[JSX em React]], podendo desenvolver o HTML dentro do JS. Claro que como estamos utilizando JS, podemos misturar conceitos de programação que não existem em HTML, como a criação de variáveis.
Exemplo:
```jsx
import './App.css';

function App() {

	let nome = "Daniel"

	return (
	
	<div className="App">
	<h1> Hello, {nome}</h1>
	</div>
	
	);
}

export default App;
```

 