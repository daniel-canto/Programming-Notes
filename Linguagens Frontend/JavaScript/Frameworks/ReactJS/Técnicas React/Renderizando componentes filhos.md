#frontend/javascript/frameworks/reactjs/tecnicas_react/renderizando_componentes_filhos 

Vamos supor, que estamos criando um componente como um container, que naturalmente irá conter outros componentes filhos, para renderizarmos o conteúdo dentro do componente pai, precisamos utilizar uma [[Componentes#O que são props?|props]] especial, que seria a `props.children`.
Em código, seria dessa forma:
```jsx
<Container>
  <Routes>
    <Route path="/" element={<Home />} />
    <Route path="/company" element={<Company />} />
    <Route path="/contact" element={<Contact />} />
    <Route path="/newproject" element={<NewProject />} />
  </Routes>
</Container>;
```
No código acima, estamos dentro do [[Arquivos base do React#./src/app.js|app.js]], criamos um componente chamado "Container" para padronizarmos e reutilizarmos mais o nosso layout.
Com isso em mente, é óbvio que precisamos renderizar tudo o que está dentro da tag `<Container/>`. Portanto, para isso, utilizamos a [[Componentes#O que são props?|props]] especial children no componente pai, dessa forma:
```jsx
import styles from "./Container.modules.css";

function Container(props) {
  return <div>{props.children}</div>;
}

export default Container;

```
Sem essa props, nada que está dentro do componente `Container` será exibido.