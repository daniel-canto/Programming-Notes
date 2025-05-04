#frontend/javascript/frameworks/reactjs/tecnicas_react/state_lift 

```table-of-contents
```

### O que é?
~={green}É uma técnica que é utilizada quando dois ou mais [[Componentes|componentes]] precisam compartilhar o mesmo dado=~. Em vez de cada componente manter seu próprio estado, você move esse estado para o componente pai comum mais próximo e passa o valor e as funções de atualização para os filhos através das props. Ou seja,~={green} seria equalizar o estado para todos os componentes através de seu pai, definindo quem usa e quem define (com [[Hooks#useState|useState]])=~.


---
### Como utilizar?
Seu uso é bem simples. Para isso, vou explicar em detalhes o fluxo dessa técnica.

 **Componente pai**: para esse exemplo, vou utilizar o [[Arquivos base do React#./src/app.js|app.js]] como exemplo de componente pai, porém poderia muito bem ser qualquer outro. 
```jsx
import { useState } from "react";
import "./App.css";
import SeuNome from "./components/SeuNome";
import Saudacao from "./components/Saudacao";

function App() {
  const [nome, setNome] = useState();

  return (
    <div className="App">
      <h1>State Lift</h1>
      <SeuNome setNome={setNome} />
      <Saudacao nome={nome} />
    </div>
  );
}

export default App;

```
Como pudemos ver, fizemos o seguinte no componente pai:
1. Definimos o [[Hooks#useState|useState]] no componente pai.
2. Definimos a constante responsável por armazenar o estado atual do elemento  na linha 7.
3. Criamos um componente chamado `<SeuNome/>`, onde passamos o método `setNome` (responsável por setar o estado atual do elemento) para esse componente, tudo isso na linha 12.

Agora, o próximo passo é dentro do componente filho responsável por definir o estado.
```jsx
function SeuNome({ setNome }) {
  return (
    <div>
      <p> Digite o seu nome</p>
      <input
        type="text"
        onChange={(e) => setNome(e.target.value)}
        placeholder="Digite seu nome"
      />
    </div>
  );
}

export default SeuNome;

```
Como pudemos ver, passamos o método `setNome` como uma props dentro do componente filho, portanto:
1. Cada interação de mudança do usuário sobre o <`input/`> desse componente, o estado do `nome` é atualizado utilizando o método fornecido pelo componente pai (`setNome`), dessa forma, seu estado está sendo armazenado no componente pai, porém sendo definido no componente filho `SeuNome`.

Com isso, nós podemos utilizar esse estado em qualquer componente filho do componente `App.js`, pois seu estado está armazenado nele.

Portanto, voltando ao componente pai:
```jsx
import { useState } from "react";
import "./App.css";
import SeuNome from "./components/SeuNome";
import Saudacao from "./components/Saudacao";

function App() {
  const [nome, setNome] = useState();

  return (
    <div className="App">
      <h1>State Lift</h1>
      <SeuNome setNome={setNome} />
      <Saudacao nome={nome} />
    </div>
  );
}

export default App;

```
Como podemos ver na linha 13, estamos chamando outro componente filho do `app.js`, e estamos passando pela props o estado atual de `nome`.
Portanto, seu uso dentro desse componente, seria assim:
```jsx
function Saudacao({ nome }) {
  function Saudar(nome_pessoa) {
    return (
      <div>
        <p> Saudações, {nome_pessoa}</p>
      </div>
    );
  }

  return Saudar(nome);
}

export default Saudacao;

```
Como podemos, criamos uma função dentro desse componente onde o estado atual do `nome` é passado para a função interna do componente filho `Saudar`, onde seu retorno uma estrutura HTML que imprime o texto de saudação com o nome digitado pelo usuário.

Portanto, esse seria o conceito de State Lift. Claro que ele poderia ser utilizado de outras formas, nesse caos foi só um pequeno exemplo.