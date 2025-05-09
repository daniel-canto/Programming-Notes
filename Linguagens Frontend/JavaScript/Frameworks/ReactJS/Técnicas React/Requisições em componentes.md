#frontend/javascript/frameworks/reactjs/tecnicas_react/requisicoes_em_componentes

As requisições podem ser feitas utilizando algumas sintaxes específicas de JS, como o `fetch`.
Entretanto, em React, temos um problema peculiar:

Se fizermos uma requisição e deixarmos o código diretamente no corpo da função de um componente, a cada nova renderização, o React vai executar novamente aquele código, portanto criar outra requisição, gerando assim requisições infinitas.
Por exemplo:
```jsx
import { useState } from "react";
import Input from "../form/Input";
import Select from "../form/Select";
import SubmitButton from "../form/SubmitButton";
import styles from "./ProjectForm.module.css";

function ProjectForm({ btnText }) {
  const [categories, setCategories] = useState([]);

  fetch("http://localhost:5000/categories", {
    method: "GET",
    headers: {
      "Content-Type": "application/json",
    },
  })
    .then((resp) => resp.json())
    .then((data) => {
      setCategories(data);
    })
    .catch((err) => console.log(err));

  return (
    <form className={styles.form}>
      <Input
        type="text"
        text="Nome do projeto"
        name="name"
        placeholder="Insira o nome do projeto"
      />
      <Input
        type="number"
        text="Orçamento do projeto"
        name="budget"
        placeholder="Insira o orçamento total"
      />
      <Select
        name="category_id"
        text="Selecione a categoria"
        options={categories}
      />
      <SubmitButton text={btnText} />
    </form>
  );
}

export default ProjectForm;
```
Aqui, fizemos uma requisição para coletar as categorias e enviá-las para um componente de campo `select`, entretanto, dessa forma a requisição seria infinita por sua chamada estar dentro do corpo do componente, sem nenhum controle.

Para obter esse controle e evitar esse problema, podemos utilizar o [[Hooks#useEffect|hook useEffect]], dessa forma:
```jsx
function ProjectForm({ btnText }) {
  const [categories, setCategories] = useState([]);

  useEffect(() => {
    fetch("http://localhost:5000/categories", {
      method: "GET",
      headers: {
        "Content-Type": "application/json",
      },
    })
      .then((resp) => resp.json())
      .then((data) => {
        setCategories(data);
      })
      .catch((err) => console.log(err));
  }, []);

  return (
    <form className={styles.form}>
      <Input
        type="text"
        text="Nome do projeto"
        name="name"
        placeholder="Insira o nome do projeto"
      />
      <Input
        type="number"
        text="Orçamento do projeto"
        name="budget"
        placeholder="Insira o orçamento total"
      />
      <Select
        name="category_id"
        text="Selecione a categoria"
        options={categories}
      />
      <SubmitButton text={btnText} />
    </form>
  );
}
```
Com isso, o problema das requisições infinitas irá para, pois o array vazio `[]` presente na linha 16, diz que esse efeito só ser executado um vez, logo após o componente ser montado na tela. Se você colocasse uma variável dentro do array, o efeito poderia ser executado novamente toda vez que alguma dessa variáveis mudar de valor.
