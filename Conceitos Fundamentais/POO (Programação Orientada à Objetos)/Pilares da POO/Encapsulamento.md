#conceitos_fundamentais/poo/pilares_da_poo/encapsulamento 

```table-of-contents
```
### O que é Encapsulamento?
O conceito de encapsulamento em POO é um pilar da POO, onde consiste em ~={green}esconder os detalhes internos de uma classe, como seus atributos e a implementação de seus métodos, e expor apenas o que é necessário para o uso externo=~, normalmente por meio de métodos públicos específicos usando [[Interfaces|interfaces]] ou por [[Métodos e Atributos#Métodos Acessores (Encapsulamento)|métodos acessores (getters e setters)]]. Isso garante o controle e a segurança dos dados de um objeto, protegendo ele de alterações indevidas.
Com essa ocultação, podemos alterar toda a lógica interna se necessário, por exemplo: temos um sistema onde o nosso sistema passa um documento e ele quer extrair seus dados. Para isso, estamos utilizando a biblioteca Y, porém, essa biblioteca irá ser descontinuada, tendo que alterar para a biblioteca X. ~={green}Com o conceito de encapsulamento, essa troca da lógica interna pouco importa, pois o resultado que o código exterior verá será o mesmo.=~

### Resumo
O encapsulamento é um dos pilares da programação orientada a objetos (POO) que consiste em:

1. **Ocultar detalhes internos**: Atributos e métodos de implementação são declarados como `private` ou `protected`, restringindo o acesso direto de fora da classe.
    
2. **Expor uma interface controlada**: Métodos públicos (`getters`, `setters` ou outros) são usados para interagir com os dados internos, garantindo segurança e controle.
    
3. **Permitir alterações internas sem impacto externo**: A lógica interna da classe pode ser modificada (como trocar bibliotecas) desde que a interface pública permaneça a mesma.