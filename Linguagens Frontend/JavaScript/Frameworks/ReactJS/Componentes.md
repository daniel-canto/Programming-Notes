#frontend/conceitos_de_frontend/componentes 

```table-of-contents
```

### O que é um componente?
São os blocos fundamentais para construir interfaces. ~={green}Eles funcionam como peças de lego, sendo independentes e reutilizáveis=~, podendo ser combinados para formar aplicações completas.

~={green}De forma conceitual, um componente é como uma função JavaScript que aceita entradas (chamadas de [[Componentes#O que são props?|props]]) e retorna elementos React descrevendo o que deve aparecer na tela=~. Tudo isso utilizando [[JSX]]. Por exemplo:
```jsx
function Welcome(props) {
  return <h1>Olá, {props.name}</h1>;
}
```

Um exemplo de componente, seria o [[Arquivos base do React#./src/app.js|App.js]], que é um componente, sendo um dos principais.

### Como criar um componente?
Para isso, precisamos criar um arquivo de componente e depois importá-lo onde vamos utilizar. Normalmente, criamos esses arquivos em uma pasta chamada `Components` dentro da pasta `src`. 
Normalmente, quando criamos um arquivo, colocamos suas letras iniciais maiúsculas, como uma classe.
Sempre começamos o desenvolvimento do componente com uma função, com o mesmo nome do arquivo e com o seu `export`. Dessa forma:
```jsx
function HelloWorld() {

}

export default HelloWorld
```

O export serve para tornar esse componente visível, assim podendo ser importado em outras partes do projeto.

Com isso, a criação do componente no fim poderia ser assim, de forma simples:
```jsx
function HelloWorld() {

	return (
		<div>
			<h1> Meu primeiro componente</h1>
		</div>
	)
}

export default HelloWorld
```

O próximo passo, seria importar esse componente em alguma parte do nosso projeto. Podemos fazer isso utilizando o `import` no arquivo desejado, por exemplo no App.js:
```jsx
import './App.css';
import HelloWorld from './components/HelloWorld';
  
function App() {

	let nome = String
	nome = "Daniel G"

	return (
		<div className="App">	
			<HelloWorld/>
		</div>
	);
}

export default App;
```
O código acima, demonstra que importamos o nosso componente e o utilizamos como se fosse uma tag HTML, que é assim que deve ser feito.
Claro que um componente pode ser importado em outro componente, e a lógica é a mesma.

### O que são props?
Props é uma abreviação para propriedades, ~={green}elas permitem que componentes sejam reutilizáveis e dinâmicos, já que cada instância de um componente pode receber valores diferentes através das props=~.

Quando você usa um componente e passa atributos para ele no [[JSX em React|JSX]], esses atributos são agrupados em um objeto chamado `props`, que é recebido como argumento na função (ou acessado via `this.props` em componentes de classe). Por exemplo:
```jsx
// Frase.js
function Frase(props){

	return (
		<div>
			<p> Isso é um exemplo de props, caro {props.name}</p>
		</div>
	)
}

export default Frase
```

```jsx
// Uso do componente com props
<Frase name="Daniel"/>
```

Vale ressaltar, que as props são apenas para leitura, para obter o valor. Modificá-lo não é permitido.

Com o uso de structuring do JS, podemos simplificar a definição das props, dessa forma:
```jsx
function Pessoa({nome, idade, profissao, foto}){

	let placeholder = nome + " placeholder image"

	return (
		<div>	
			<img src={foto} alt={placeholder}/>			
			<h2>Nome: {nome}</h2>			
			<p>Idade: {idade}</p>		
			<p>Profissão: {profissao}</p>	
		</div>
	)

}

export default Pessoa
```