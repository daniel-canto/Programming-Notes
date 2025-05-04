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