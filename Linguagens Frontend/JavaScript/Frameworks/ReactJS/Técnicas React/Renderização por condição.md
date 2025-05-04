#frontend/javascript/frameworks/reactjs/tecnicas_react/renderizacao_por_condicao 


É uma técnica que consiste em exibir ou ocultar elementos, componentes ou trechos da interface de acordo com determinadas condições do estado da aplicação, variáveis ou props. Ou seja, você controla dinamicamente o que aparece na tela de acordo com o contexto ou ações do usuário.
Podemos utilizar o [[Hooks#useState|useState]] para criar as condições.

Abaixo, está um exemplo simples do seu uso:
```jsx
import { useState } from "react";

function Condicional() {
  function enviarEmail(e) {
    e.preventDefault();
    setUserEmail(email);
    console.log(userEmail);
  }

  function limparEmail() {
    setUserEmail("");
    setEmail("");
  }

  const [email, setEmail] = useState();
  const [userEmail, setUserEmail] = useState();

  return (
    <div>
      <h2>Cadastre o seu email</h2>
      <form>
        <input
          type="email"
          value={email}
          placeholder="Digite o seu email..."
          onChange={(e) => setEmail(e.target.value)}
        ></input>
        <button type="submit" onClick={enviarEmail}>
          Enviar email
        </button>
      </form>
      {userEmail && (
        <div>
          <p>O email do usuário é: {userEmail}</p>
          <button onClick={limparEmail}>Limpar email</button>
        </div>
      )}
    </div>
  );
}

export default Condicional;

```
Nesse caso, podemos observar que a condição se encontra na linha 32, onde ela será verdadeira caso a constante  `userEmail` estiver preenchida, e se a condição for verdadeira, será exibida uma nova estrutura HTML que irá mostrar o email digitado e um novo botão para limpar esse email. 
Ao criar condições no HTML (qualquer código JS dentro do JSX) precisamos utilizar as chaves `{}`.