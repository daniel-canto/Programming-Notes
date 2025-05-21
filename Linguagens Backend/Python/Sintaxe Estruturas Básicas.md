#backend/python/sintaxe_estruturas_básicas
Aqui está registrado apenas os fundamentos mais básicos do Python, coisas bem simples e comuns.

```table-of-contents
```

### Docstrings e comentários
    
Ao usar `#` antes no começo de uma linha, essa linha irá se tornar um comentário e o interpretador irá ignorar apenas essa linha.

O conceito de docstring é diferente, pois ele funciona como um campo de comentário, onde todas as linhas contidas dentro dessa “estrutura”. Entretanto, o interpretador lê essas linhas.
    
### Input
    
Os inputs em Python, tem por padrão a string como tipagem de dados padrão. Dessa forma, precisamos usar um cast pra determinar qual será o tipo de dado dela, dessa forma:

```python
idade = int( input("Digite sua idade: ") )
print(idade)
```

### Print (output)
    
Para concatenar texto e o valor das variáveis, fazemos da seguinte maneira:

```python
idade = int( input("Digite sua idade: ") )
idade = idade + 3
print("Sua idade é: ", idade)
```

Podemos fazer algumas modificações na exibição de uma mensagem, por exemplo: `print(12, 34, sep=”-")`

Nesse código, ele separa os elementos 12 e 34 por um ‘-’. Para mais modificações, podemos pesquisar na internet.
    
### Condicionais
    
Em Python, não temos o else if, apenas o elif, que tem a mesma função.

![[Pasted image 20250316175713.png]]

### Estruturas de repetição

###### While
O `while` possuí a mesma estrutura e conceito em relação à outras linguagens:

```python
c = 1
while c < 10:
	c = c + 1

print(c)
```

O resultado desse código seria `c = 10` .
###### Estrutura for
Esse for, funciona de forma diferente do convencional. Para se declarar essa estrutura, fazemos o seguinte código:
    
```python
    for x in range(5)
    ```
    
Nessa estrutura o `x` seria o contador, enquanto `range(5)` seria a quantidade de repetições. Caso o `x` fosse exibido a cada repetição, ele começaria em 0, o resultado seria assim: [0 1 2 3 4].
    
Nessa estrutura, podemos também trocar o `range(5)` por uma variável.
    
Assim como uma work area em ABAP, nós podemos fazer a estrutura iterar sobre uma lista de objetos por exemplo:
    
```python
     for usage in self.user_usages:
    ```
    
Dentro desse for, a manipulação dos campos seria assim:

`print(usage.tokens_used)`

Vale lembrar, que o ponto é usado em uma lista de objetos. Se fosse uma lista de dicionários, usaríamos o colchete, assim:

`print(usage['tokens_used'])`

    
### Dicionário e Lista de dicionários
    
Os dicionários se assemelham às structs aprendidas em C. Dessa forma, cada dicionário possui chaves e valores, como no exemplo abaixo:

```python
pessoa =  {
	"Nome": "Daniel Gomes",
	"Idade": 19,
	"Profissao": "Desenvolvedor de Sistemas"
}

print(pessoa['Nome'])
print(pessoa['Idade'])
print(pessoa['Profissao'])
```

Por outro lado a lista de dicionários é justamente uma lista de dicionários, ou seja, ele armazena vários dicionários em apenas uma estrutura organizada, para evitar criar muitas listas.

```python
pessoas = [
	{"Nome": "Daniel Gomes", "Idade": 19, "Profissao": "Desenvolvedor de Sistema"},
	{"Nome": "José Alves", "Idade": 45, "Profissao": "Marketing Dgital"},
	{"Nome": "Maria Eduarda", "Idade": 19, "Profissao": "Recursos Humanos"}
]
```

Nesse caso, cada dicionário possui suas próprias chaves.

<aside> 💡

**Por boa prática, quando a estrutura é um dicionário, colocamos no singular e quando é uma lista de dicionários, colocamos no plural.**

</aside>

### Funções
    
Assim como a maioria das outras linguagens, as funções em Python são declaradas da mesma forma lógica. Entretanto, não precisamos passar o tipo de dado e não é obrigatório haver um retorno. Abaixo, segue um exemplo simples do uso de funções:

```python
def soma(n1, n2):
	R = n1 + n2 
	return R

n1 = 2
n2 = 3
resposta = soma(n1, n2)
print(resposta)
```
