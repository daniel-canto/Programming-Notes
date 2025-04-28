#conceitos_fundamentais/poo/pilares_da_poo/polimorfismo 

```table-of-contents
```

### O que é polimorfismo
Em POO, o polimorfismo permite que diferentes objetos respondam à mesma mensagem (ou chamada de método), cada um à sua maneira, de acordo com sua própria implementação.

Ou seja, ~={green}a partir da [[Métodos e Atributos#O que é uma assinatura de método?|assinatura de um método]], podemos reutilizar o mesmo método, mas com implementações diferentes=~.

Portanto, ~={green}o polimorfismo ocorre quando uma subclasse redefine (sobrescreve) um método da superclasse, fornecendo uma implementação específica (especialização) para aquele método=~. Dessa forma, a chamada ao método em tempo de execução será direcionada para a versão correspondente ao tipo real do objeto.

Vale ressaltar que os dois métodos poderiam ter o mesmo nome, mas se tiverem parâmetros diferentes, terão [[Métodos e Atributos#O que é uma assinatura de método?|assinaturas]] diferentes e poderão até mesmo coexistir na mesma classe.

----
### Exemplo
Imagine uma classe chamada `Funcionario` com um método `calcularSalario()`. As subclasses `Vendedor` e `Diretor` podem sobrescrever esse método para calcular o salário de formas diferentes. Ao chamar `calcularSalario()` para cada tipo de funcionário, o comportamento será específico da subclasse, mesmo usando uma referência do tipo `Funcionario`.

----
### Vantagens
- **Flexibilidade e reutilização de código:** Permite criar um código mais genérico e modular, facilitando a manutenção e evolução do sistema.

- **Redução de duplicidade:** Evita a repetição de código, já que o comportamentos comuns podem ser definidos na superclasse e especializados nas subclasses.

- **Facilidade de manutenção:** Alterações em subclasses não afetam o código que utiliza referências da superclasse.

----
### Tipos de polimorfismo
Existem alguns tipos de polimorfismo que podem ser usados em casos específicos.

##### Polimorfismo de sobrescrita (dinâmico)
~={green}Ocorre quando os métodos com a mesma [[Métodos e Atributos#O que é uma assinatura de método?|assinatura]] são implementados de formas diferentes nas subclasses.=~ A decisão de qual método executar é feita em runtime, com base no tipo real do objeto.
Vale ressaltar que ela só pode ocorrer uma vez em uma mesma classe, assim, tendo que ser utilizada em classes diferentes.

Na maioria das linguagens, quando formos implementar esses métodos, usamos anotações como `@override` ou `@sobrepor`. Isso varia de linguagem para linguagem.

##### Polimorfismo de sobrecarga (estático)
~={green}Ocorre quando métodos com o mesmo nome, mas [[Métodos e Atributos#O que é uma assinatura de método?|assinaturas]] diferentes, existem na mesma classe, ou quando uma subclasse altera a assinatura, modificando parâmetros.=~ A escolha do método é feita em runtime, com base nos parâmetros utilizados.
  