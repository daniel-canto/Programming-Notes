 #conceitos_fundamentais/poo/conceitos_tecnicos/metodos_e_atributos 

```table-of-contents
```

### Métodos
Teoricamente falando,~={green} os métodos seriam o comportamento de um objeto ou classe=~, como citado anteriormente na seção das classes, seriam ações como  rabiscar, tampar, destampar, contar, subtrair, verificar e etc.
Para os métodos, existe um conceito chamado "[[Métodos e Atributos#Modificadores de visibilidade|modificadores de visibilidade]]", que indicam o nível de acesso aos componentes internos de uma classe.

##### O que é uma assinatura de método?
~={green}É o conjunto de informações que identifica de forma única um método dentro de uma classe. Ela é composta pelo nome do método e pela lista de parâmetros (tipos, quantidade e ordem dos parâmetros)=~. Isso permite que métodos com o mesmo nome, mas com parâmetros e implementações diferentes, coexistam dentro de uma mesma classe ou entre uma classe e suas superclasses, conhecido como [[Polimorfismo#Polimorfismo de sobrecarga (estático)|sobrecarga de métodos]], como visto em polimorfismo.
 
##### Métodos Acessores (Encapsulamento)
~={green}São métodos especiais usados para acessar (get) ou modificar (set) os valores dos [[#Privado (-)|atributos privados]] de uma classe, de forma mais controlada=~. ~={green}Eles são popularmente conhecidos como getters e setters=~.
O uso desses métodos é diretamente ligado ao conceito de [[Encapsulamento]], que tem como objetivo proteger os dados internos do objeto, garantindo controle e evitando acessos diretos.

##### Método Construtor
Ele é um método especial de uma classe que é chamado automaticamente no momento em que um novo objeto dessa classe é criado. ~={green}Sua função é garantir que o objeto seja inicializado corretamente, atribuindo valores iniciais aos seus atributos e realizando qualquer outra configuração necessária para o funcionamento do objeto=~.
Com isso, você pode definir atributos em hard code, ou passar parâmetros para o construtor, assim o objeto será criado com os dados passados pelo parâmetro do construtor.
**Algumas características são:**
* O construtor tem o mesmo nome da classe.
* Não possui retorno, nem mesmo void.
* É executado sempre que um objeto é criado.
* Pode receber parâmetros, permitindo criar objetos com valores já definidos.
* Uma classe pode ter vários construtores, diferenciados pela quantidade e tipos de parâmetros, isso se chama sobrecarga de construtores.
**~={red}Nem todas as linguagens de programação podem seguir à risca essas características.=~**
Além dos atributos, ~={green}o construtor também pode chamar outros métodos ao inicializar um objeto=~. Isso é muito útil para realizar validações de dados, como em documentos.

##### Método Abstrato
É um método que é declarado, mas não é implementado na classe progenitora (que seria a classe mãe, como visto em [[Herança]]). Só pode ser utilizado em [[Interfaces|interfaces]] e [[Classes, Objetos e Instâncias#O que é uma classe abstrata?|classes abstratas]].

##### Método Final
Ele não pode ser sobrescrito pelas suas sub-classes, ou seja, não há brecha para o uso de [[Polimorfismo#O que é polimorfismo|polimorfismo]]. Ele é obrigatoriamente herdado.

##### Método Estático
- São métodos associados à classe, e não a uma instância específica.
- Não têm acesso direto aos atributos de instância nem ao próprio objeto.
- Podem ser chamados diretamente pelo nome da classe, sem necessidade de criar um objeto.
- São úteis para funções utilitárias ou operações que não dependem do estado de uma instância.
* Em linguagens como Java, C# e Python, são declarados com o modificador `static` (ou decorador `@staticmethod` em Python).

##### Método de Instância
* São métodos que operam sobre os atributos de instância de um objeto, ou seja, dependem dos valores específicos de cada instância. 
* Para eles serem chamados, é necessário criar um objeto ([[Classes, Objetos e Instâncias#O que é uma instância?|instância]])
* Permitem acessar e modificar o estado da instância, ou seja, os valores dos atributos daquele objeto específico

---
### Atributos
Em teoria, os ~={green}atributos representam as características de um objeto,=~ como peso, altura, cor de pele, cor dos olhos, sexo, idade, nome e etc.
Em resumo eles carregam informações dos objetos.
Assim como os métodos, no atributo existe um conceito chamado "[[Métodos e Atributos#Modificadores de visibilidade|modificadores de visibilidade]]", que indicam o nível de acesso aos componentes internos de uma classe.

### Modificadores de visibilidade
Os modificadores de visibilidade servem para~={green} indicar o nível de acesso aos componentes internos de uma classe, ou seja, seus atributos e métodos.=~ Isso significa que um determinado modificador pode deixar um método ou atributo invisível para o outras partes do código por exemplo.
Existem 3 tipos de modificadores, em UML (Unified Modeling Language) eles são representados com os seguintes símbolos: 
##### Público (+)
Esse modificador normalmente vem como padrão nos atributos e métodos, ele deixa um componente visível para todo o código, ou seja, ~={green}qualquer parte do meu código pode utilizar um atributo ou método público=~. Normalmente são informações que todos podem acessar.

##### Privado (-)
Assim como o nome diz, esse modificador priva a classe, onde o uso de um componente privado ~={green}só pode ser usado pela própria classe ou se essa classe tiver um [[Encapsulamento]] que possua esse componente=~. Normalmente são dados sensíveis, como senhas ou informações bancárias.

##### Protegido (#)
Esse modificador permite que ~={green}apenas a classe atual e suas filhas (ou sub-classes) tenham acesso ao seus componentes=~. Normalmente são métodos ou atributos que ó fazem sentido dentro da hierarquia de classes.