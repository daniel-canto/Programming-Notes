#frontend/javascript/frameworks/reactjs/bibliotecas_react/react_router 

```table-of-contents
title: 
style: nestedList # TOC style (nestedList|nestedOrderedList|inlineFirstLevel)
minLevel: 0 # Include headings from the specified level
maxLevel: 0 # Include headings up to the specified level
includeLinks: true # Make headings clickable
hideWhenEmpty: false # Hide TOC if no headings are found
debugInConsole: false # Print debug info in Obsidian console
```

### O que é?
~={green}O React Router é uma biblioteca para React que permite implementar o conceito de roteamento em aplicações de página única=~ (~={blue}SPA=~). Com ele, você pode mapear URLs para componentes em React, ~={green}criando a navegação entre diferentes "páginas" da sua aplicação sem recarregar o servidor, apenas trocando o layout da aplicação=~.
Para isso, precisamos instalar essa biblioteca. 

### Como utilizar?
Para usar esse recurso, precisamos instalá-lo, dessa forma
```bash
npm install react-router-dom
```

Agora, precisamos configurar o nosso projeto para o React Router funcionar.
Para isso, no [[Arquivos base do React#./src/app.js|app.js]], precisamos fazer algumas importações:
```jsx
import { BrowserRouter as Router, Routes, Route, Link } from 'react-router-dom';
```

Agora, nós envolvemos toda a nossa aplicação dentro da tag `<Router>...</Router>`, pois é ele quem vai adaptar toda a minha aplicação para usar o Router, aqui podemos definir as views (que seriam as rotas) e também componentes padrão, que farão parte de todas as views (como uma navbar ou etc).

Com isso em mente, vamos criar as nossas rotas:

Primeiro, criamos a nossa barra de navegação:
```jsx
import "./App.css";
import { BrowserRouter as Router, Routes, Route, Link } from "react-router-dom";

function App() {
  return (
    <Router>
      <ul>
        <li>
          <Link to="/">Home</Link>
        </li>
        <li>
          <Link to="/empresa">Empresa</Link>
        </li>
        <li>
          <Link to="/contato">Contato</Link>
        </li>
      </ul>
    </Router>
  );
}

export default App;

```
Essa tag `<Link>...</Link>` seria como a tag `<a>` do HTML padrão, porém essa é a tag especial para fazer o roteamento do projeto por baixo dos panos, então nesse caso ela funciona como uma navbar.
Diferente de outros frameworks frontend, normalmente nós decretamos as urls em arquivos separados, entretanto em React, definimos as rotas tudo no [[Arquivos base do React#./src/app.js|app.js]] mesmo.

~={orange}OBS: =~Vale ressaltar, que a tag `<Router>...</Router>` virou a nossa tag pai principal da aplicação (ao invés de uma simples `<div>`), portanto, quando definimos alguma estrutura HTML ou algum componente, ele vai se replicar para todas as views. Por isso nós simplesmente definimos a navbar no começo do router, pois ela vai persistir em todas as views.

Com isso, nós já definimos as rotas. Agora precisamos criar as páginas em si, que na verdade seriam os componentes (views) que vão representar essa página.
Para isso, na pasta `src` do projeto, criamos uma nova pasta chamada `pages` e criamos os componentes (que aqui se chamam views) das nossas novas páginas, sempre com os nomes iguais aos definidos no `<Link>...</Link>`.

Com isso criado, precisamos importar as nossas views recém criadas como um componente dentro do nosso [[Arquivos base do React#./src/app.js|app.js]]:
```jsx
import Home from './pages/Home.';
import Empresa from './pages/Empresa';
import Contato from './pages/Contato';
```

Agora dentro da tag `<Router>...</Router>`, precisamos criar uma tag chamada `<Routes>...</Routes>` onde dentro dela iremos associar as URLs com as suas respectivas views, utilizando a tag `<Route>...</Route>`, dessa forma:
```jsx
<Router>
  <ul>
    <li>
      <Link to="/">Home</Link>
    </li>
    <li>
      <Link to="/empresa">Empresa</Link>
    </li>
    <li>
      <Link to="/contato">Contato</Link>
    </li>
  </ul>
  <Routes>
    <Route path="/" element={<Home />} />
    <Route path="/empresa" element={<Empresa />} />
    <Route path="/contato" element={<Contato />} />
  </Routes>
</Router>;
```
Com isso, o roteamento já está funcionando.

Agora, como boa prática, seria ideal nós deixarmos a navbar em um componente, dessa forma, criando esse componente normalmente dentro da pasta `components`, pois a navbar não é uma view.
Para uma melhor organização de pasta, dentro de `components`, criamos uma pasta chamada `layout`, que contém todo o layout padrão da aplicação, como o footer e a navbar. 
```jsx
import { Link } from "react-router-dom";

function Navbar() {
  return (
    <ul>
      <li>
        <Link to="/">Home</Link>
      </li>
      <li>
        <Link to="/empresa">Empresa</Link>
      </li>
      <li>
        <Link to="/contato">Contato</Link>
      </li>
    </ul>
  );
}

export default Navbar;
```
Com isso, até podemos tirar o `Link` do import do [[Arquivos base do React#./src/app.js|app.js]], e claro, poderíamos estilar a navbar ao nosso gosto.

Agora, vamos estilizar a navbar usando o [[CSS Modules]], dessa forma:
`Navbar.modules.css`:
```css
.list {
	display: flex;
	list-style: none;
}

.item{
	margin-right: 1em;
}
```

`Navbar.js`:
```jsx
import { Link } from "react-router-dom";
import styles from "./Navbar.module.css";

function Navbar() {
  return (
    <ul className={styles.list}>
      <li className={styles.item}>
        <Link to="/">Home</Link>
      </li>

      <li className={styles.item}>
        <Link to="/empresa">Empresa</Link>
      </li>

      <li className={styles.item}>
        <Link to="/contato">Contato</Link>
      </li>
    </ul>
  );
}

export default Navbar;
```
Dessa forma, nós temos uma navbar funcional e estilizada em todo o nosso projeto.

Para avançar nesse tópico, podemos criar o componente do footer também e adicionar no final da aplicação, assim:
```jsx
function Footer() {
  return <footer>Rodapé</footer>;
}

export default Footer;

```

Com tudo isso, o [[Arquivos base do React#./src/app.js|app.js]] ficaria assim:
```jsx
import "./App.css";
import { BrowserRouter as Router, Routes, Route, Link } from "react-router-dom";
import Home from "./pages/Home.";
import Empresa from "./pages/Empresa";
import Contato from "./pages/Contato";
import Navbar from "./components/layout/Navbar";
import Footer from "./components/layout/Footer";

function App() {
  return (
    <Router>
      <Navbar />
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/empresa" element={<Empresa />} />
        <Route path="/contato" element={<Contato />} />
      </Routes>
      <Footer />
    </Router>
  );
}

export default App;
```

Onde novamente, tanto a `<Navbar/>` quanto o `<Footer/>` serão exibidos em todas as views do projeto, por estarem dentro da tag `<Router>...</Router>`, enquanto o layout das views só serão carregas de acordo com a URL da aplicação. Portanto, isso amplia a reutilização do React.

### Conteúdos adicionais sobre o React Router
[[Hooks React Router]]