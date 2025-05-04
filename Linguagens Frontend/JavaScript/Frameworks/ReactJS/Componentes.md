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
~={green}Para isso, precisamos criar um arquivo de componente e depois importá-lo onde vamos utilizar.=~ Normalmente, criamos esses arquivos em uma pasta chamada `Components` dentro da pasta `src`. 
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

~={green}Com o uso de structuring do JS, podemos simplificar a definição das props=~, dessa forma:
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

##### Definindo tipos para as props
Podemos definir tipos para as props, fazendo um tipo de validação, definindo em um objeto chamado `propTypes` no próprio componente, havendo também a possibilidade de definir um valor padrão, onde nesse caso usamos `defaultProps`.
Exemplo de uso do PropTypes:
```jsx

// Uso - tipos númericos devem estar entre chaves.
<Item marca="Ferrari" anoLancamento={1985}/>
<Item marca="BMW" anoLancamento={1964}/>

// Arquivo do componente
import PropTypes from 'prop-types'

function Item({marca, anoLancamento}){

	return (	
		<>		
			<li>{marca} - {anoLancamento}</li>	
		</>
	)
}

// Define os tipos - Item.PropTypes seria incorreto, o P precisa ser pequeno
Item.propTypes = {
	marca: PropTypes.string,
	anoLancamento: PropTypes.number
}

export default Item
```

No exemplo acima, apenas definimos o tipo do props, mas podemos também tornar essa prop obrigatória.
###### Deixar a prop obrigatória:
```jsx
Item.propTypes = {
	marca: PropTypes.string.isRequired,
	anoLancamento: PropTypes.number
}
```

###### Valor padrão para a prop
Para isso, precisamos apenas coloca o valor dentro do structuring.
```jsx
function Item({marca = 'Faltou a marca', anoLancamento = 0})
```

##### Passando métodos (eventos) pela prop
Em React~={green}, podemos passar eventos (funções/métodos) como props para outros componentes=~. Por exemplo, nós podemos declarar uma função em um componente pai e passá-lá como prop para um componente filho. Assim, o filho pode então executar essa função em resposta a eventos (como `onClick`), permitindo que o pai reaja a ações do filho.

~={green}Essa técnica é interessante, pois normalmente, faz mais sentido você ter os métodos no componente pai=~. Por exemplo, em um contexto de E-Commerce, eu teria um card (que seria o componente pai) e os componentes filhos (botões favoritar e comprar), nesse caso faz mais sentido eu centralizar os métodos "favoritar" e "comprar" no componente pai e deixar eventos de click de cada botão dentro do componente filho, onde um desses eventos forem disparados, o método respectivo do pai será chamado.
Isso ocorre por que geralmente os produtos carregados em cada card no componente pai (o card) em loop, além disso, normalmente o componente pai já tem acesso ao contexto e dados necessários.

**Como utilizar essa técnica?**
```jsx
// Componente pai 
import Button from "./evento/Button";

function Evento() {
  // Método do componente pai.
  function meuEvento() {
    console.log("Ativando primeiro evento");
  }

  return (
    <div>
      <p> Clique para disparar um evento: </p>
      {/* Passamos o método do pai para que o filho dispare */}
      <Button event={meuEvento} text="Primeiro evento" />
    </div>
  );
}

export default Evento;

// Método filho
function Button(props){
	// Filho recebe o método que é chamado quando o evento onClick for 
	// disparado.
	return <button onClick={props.event}>{props.text}</button>
}

export default Button

```
**Resumo:**
**Componente Pai (`Evento`)**
- Define a função `meuEvento`, que será chamada quando o botão for clicado.
- Passa essa função como prop chamada `event` para o componente filho `Button`.
- Também passa a prop `text` para personalizar o texto do botão.
- 
**Componente Filho (`Button`)**
- Recebe a função via `props.event` e o texto via `props.text`.
- Usa `props.event` como handler do evento `onClick` do botão.
- Quando o botão é clicado, o método do pai é executado.