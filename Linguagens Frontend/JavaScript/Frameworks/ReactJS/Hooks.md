#frontend/javascript/frameworks/reactjs/hooks 

```table-of-contents
```

### O que é um Hook?
~={green}Os Hooks são funções especiais que permitem usar recursos como estado, ciclo de vida e contexto em componentes funcionais, sem a necessidade de classes.=~
Eles são divididos em duas categorias principais: hooks básicos (mais usados) e hooks adicionais (para casos específicos).

---
### Lista de Hooks
##### useState
~={green}Ele é responsável por permitir que componentes funcionais tenham e gerenciem estado-local, ou seja, dados que podem mudar ao longo do tempo e que afetam o que é exibido na interface=~. Este hook é muito bem aplicado com [[Eventos]], pois também podemos atrelar um evento a mudança de estado.
Em resumo, ele é ~={green}ótimo em casos como coleta de dados de um formulário=~, onde esse hook pode ser aplicado assim:
```jsx
import { useState } from "react";

function Form() {
  function cadastrarUsuario(e) {
    e.preventDefault();
    console.log(name);
    console.log(password);
    console.log("Cadastrou o usuário");
  }

  const [name, setName] = useState();
  const [password, setPassword] = useState();

  return (
    <div>
      <h1>Meu cadastro</h1>
      <form onSubmit={cadastrarUsuario}>
        <div>
          <label htmlFor="name">Nome</label>
          <input
            type="text"
            name="name"
            id="name"
            placeholder="Digite seu nome"
            onChange={(e) => setName(e.target.value)}
          ></input>
        </div>

        <div>
          <label htmlFor="password">Senha</label>
          <input
            type="password"
            name="password"
            id="password"
            placeholder="Digite a sua senha"
            onChange={(e) => setPassword(e.target.value)}
          ></input>
        </div>

        <div>
          <input type="submit" value="Cadastrar"></input>
        </div>
      </form>
    </div>
  );
}

export default Form;
```
~={green}**Explicação do código=~:** Cada vez que o usuário digita um caractere no `<input>`, o evento `onChange` é disparada. O React chama a função que você passou para esse evento, no caso:
```jsx
onChange={(e) => setName(e.target.value)}
```
Onde:
- `e` é  o evento do input.
- `e.target.value` é o valor atual do campo de texto.
A função `setName` (vinda do `useState`) é chamada com esse valor, atualizando o estado `name`com o novo texto digitado.
O mesmo vale para o campo senha.

Com isso, quando o usuário submita o formulário, o formulário dispara o evento `onSubmit`, que chama sua função `cadastrarUsuario`, onde os dados que foram coletados pelo `useState` serão utilizados.
~={green}**Em resumo:**=~
1. Usuário digita → `onChange` dispara → chama `setName` ou `setPassword` → React atualiza o estado.
2. Estado (`name` e `password`) sempre reflete o valor atual dos inputs.
3. Ao submeter o formulário, você acessa os valores diretamente das variáveis de estado.

~={green}**Vale ressaltar que podemos passar valores padrão no `useState=~`**, passando a constante no `value`, dessa forma:
```jsx
const [name, setName] = useState('Dan')

<input type="text" value={name} name="name" id="name" placeholder="Digite seu nome" onChange={(e) => setName(e.target.value)}></input>
```

##### useEffect
É um hook que permite executar efeitos colaterais em componentes funcionais, como busca de dados em uma API, manipular o DOM, configurar assinaturas de eventos ou sincronizar o componente com sistemas externos. 
Ele consegue isso, pois o React executa o efeito após a atualização do DOM, garantindo que a interface esteja atualizada antes de rodar o código do efeito.
Se necessário, a função passada ao `useEffect` pode retornar outra função, chamada de **função de limpeza** (_cleanup_), que será executada antes do efeito rodar novamente ou quando o componente for desmontado. Isso é útil para cancelar assinaturas, limpar timers ou desfazer efeitos anteriores

**Seu uso é feito da seguinte forma:**
O `useEffect` recebe dois argumentos:
1. **Uma função de efeito**: é o código que será executado após a renderização do componente. Dentro dessa função, você pode acessar props e estados atuais do componente.
2. **Um array de dependências (opcional)**: determina quando o efeito deve ser executado novamente. Se o array estiver vazio (`[]`), o efeito roda apenas uma vez, na montagem do componente. Se você omitir o array, o efeito será executado após toda renderização. Se você incluir variáveis no array, o efeito será executado sempre que alguma dessas variáveis mudar de valo.

**Exemplo de uso de `useEffect`**:
```jsx
**function ProjectForm({ btnText }) {
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
Nesse exemplo, estamos realizando uma requisição para obter as categorias cadastradas. Utilizamos o `useEffect` para que a requisição seja feita apenas em uma única renderização. Sem esse hook, a aplicação faria requisições infinitas.