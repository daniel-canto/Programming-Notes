#frontend/javascript/frameworks/reactjs/eventos

### O que é?

Os eventos em React são mecanismos que permitem capturar e responder a ações do usuário ou do sistema, como cliques, digitação, envio de formulários, entre outros. Eles funcionam igual aos eventos do DOM tradicional, mas apresentam diferenças em sua sintaxe e comportamento.

##### Características
- Ao invés de passar uma string com o nome da função, passamos uma referência direta à função do evento.
- O React utiliza o `SyntheticEvent`, que é um wrapper que normaliza o comportamento dos eventos para funcionar de maneira consistente em todos os navegadores. O objeto de evento recebido nas funções possui métodos como `preventDefault()` e `stopPropagation()`, semelhantes ao DOM nativo.
- Não precisamos usar o `addEventListener` para adicionar ouvintes de evento. 
- Para impedir o comportamento padrão, use o `event.preventDefault()` dentro do manipulador, e não retornando `false` como seria feito em JS puro.

### Como utilizar?
Abaixo, está um exemplo de como utilizar um evento `onClick`.
```jsx
// App.js
return (
	<div className="App">
		<Evento/>
	</div>
);

// Evento (componente)
function Evento() {

	function meuEvento(){	
		console.log('Ativado')	
	}
		
	return (	
		<div>		
			<p> Clique para disparar um evento: </p>			
			<button onClick={meuEvento}> Disparar </button>		
		</div>	
	)
}

export default Evento
```

Claro que podemos trabalhar com [[Componentes#O que são props?|props]] dentro dos eventos, onde seu uso é igual.
Por exemplo:
```jsx
// App.js
return (
	<div className="App">
		<Evento numero={1}/>
	</div>
);

// Evento (Componente que contém o evento)
function Evento({numero}) {

	function meuEvento(){	
		console.log(`Ativado #${numero}`)	
	}
	
	return (	
		<div>		
			<p> Clique para disparar um evento: </p>			
			<button onClick={meuEvento}> Disparar </button>		
		</div>	
	)
}

export default Evento
```

##### Como criar um formulário em React?
Como exemplo, vou criar primeiro um componente de um formulário simples, que contenha tanto o corpo do formulário quanto sua função de evento, dessa forma:
```jsx 

// Componente do formulário
function Form(){

	function cadastrarUsuario(e){
		e.preventDefault()
		console.log("Cadastrou o usuário")
	}
	
	return (	
		<div>	
			<h1>Meu cadastro</h1>	
			<form onSubmit={cadastrarUsuario}>	
				<div>			
					<input type="text" placeholder="Digite seu nome"></input>			
				</div>	
		  	
				<div>	
					<input type="submit" value="Cadastrar"></input>			
				</div>	
			</form>	
		</div>	
	)
}

export default Form
```
Por ser um formulário, precisamos utilizar o `preventDefault`, pois ao o submeter um formulário, o comportamento padrão do navegador é recarregar a página. Usando `event.preventDefault()`, você pode evitar esse recarregamento e, assim, tratar o envio dos dados manualmente, como fazer validações ou enviar informações via JavaScript antes de realmente enviar ao servidor.

Na sua execução, seria assim:
```jsx
<div className="App">
	<Form/>
</div>
```

