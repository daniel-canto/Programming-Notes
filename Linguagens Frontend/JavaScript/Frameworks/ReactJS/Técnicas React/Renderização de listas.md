#frontend/javascript/frameworks/reactjs/tecnicas_react/renderizacao_de_listas 

Para renderizarmos uma lista em React, podemos utilizar as seguintes técnicas:
- Utilizar um array
- Depois utilizar a ~={blue}função map=~ para percorrer cada um dos itens.
- Podemos unir a [[Renderização por condição]] com a renderização de listas.

Para renderizarmos uma lista, é muito simples, segue o código:

```jsx
function Outralista({ itens }) {
  return (
    <>
      <h3>Lista de coisas boas</h3>
      {itens.length > 0 ? (
        itens.map((item, index) => <p key={index}>{item}</p>)
      ) : (
        <p> Não há itens na lista. </p>
      )}
    </>
  );
}

export default Outralista;

```

Acima, nós temos o nosso componente de lista. Vou explicar o fluxo dele agora.
1. **Recebe uma lista pela props**
2. **Verifica se a lista está vazia:** isso é feito usando um if ternário no [[JSX em React|jsx]], onde se a lista estiver vazia, a mensagem "Não há itens na lista" será exibida.
3. **Exibe cada elemento da lista**: ele exibe cada elemento utilizando a ~={blue}função map=~, então passamos a nossa lista como parâmetro dessa função e depois exibimos cada elemento.
4. O React requere o uso da `key` em cada elemento, pois o React precisa identificar de forma única cada item para posteriores operações. Como nesse exemplo específico eu utilizei uma lista (array) simples e hard coded, eu utilizei o index da lista como chave. Normalmente, num projeto real, utilizaríamos um id e certamente não seria uma lista, mas sim um ~={blue}dicionário=~.

Dessa forma, esse componente seria chamado dessa forma no [[Arquivos base do React#./src/app.js|app.js]] 
```jsx
import "./App.css";
import Outralista from "./components/Outralista";

function App() {
  const meusItens = ["React", "Vue", "Angular"];

  return (
    <div className="App">
      <h1> Renderização de listas</h1>
      <Outralista itens={meusItens} />
      <Outralista itens={[]} /> // Teste lista vazia, para gerar o alerta.
    </div>
  );
}

export default App;

```

Para utilizar essa técnica com dados vindos de uma API (como o seu backend do projeto), nós podemos utilizar a técnica descrita nessa anotação [[Requisições em componentes]].
A lógica seria a mesma, mas usando dados vindos direto de um backend.