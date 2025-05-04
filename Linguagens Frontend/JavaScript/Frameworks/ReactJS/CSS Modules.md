#frontend/conceitos_de_frontend/css_modules 

```table-of-contents
```

### O que é CSS Modules?
O CSS em React pode ser adicionado globalmente pelo arquivo [[Arquivos base do React#.src/index.css|index.css]].
Entretanto, é possível usar o CSS apenas em um componente, utilizando o `CSS Modules`. 
Isso é muito útil para manter certo padrão na aplicação, pois podemos padronizar por exemplo o fundo de todas as telas aplicando essa propriedade no CSS global, enquanto colocamos cores de fundo específicas para determinados componentes.

---
### Como utilizar?
Para alterarmos o CSS global, nós trabalhamos dentro do arquivo [[Arquivos base do React#.src/index.css|index.css]], assim toda a aplicação vai seguir um padrão.

Entretanto, para utilizar isso em componentes, criamos o arquivo css para o componente dessa forma: `<nome_componente>.module.css`.
Dentro desse arquivo, podemos criar as classes e até mesmo os ids do CSS. Para utilizar essa estilização dentro do componente, precisamos importá-lo, dessa forma: `import styles from './Frase.module.css'`. O `styles` funciona como um [[Componentes#O que são props?|props]], onde ele é um objeto que condensou todas as classes e ids em propriedades.
Portanto, para utilizar essa propriedade em um elemento, utilizamos ela assim:
```jsx
import styles from './Frase.module.css'

function Frase(props){

	return (
		<div className={styles.fraseContainer}>
			<p> Isso é um exemplo de props, caro {props.name}</p>
		</div>
	)
}

export default Frase
```