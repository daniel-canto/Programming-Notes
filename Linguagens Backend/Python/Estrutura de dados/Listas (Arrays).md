#backend/python/estrutura_de_dados/listas
Em primeiro lugar, uma lista em Python é o equivalente à um array em linguagens de programação mais famosas, como o C e o JS.

Em Python, uma lista é um [[Tipos Mutáveis e Imutáveis#Objetos Mutáveis|objeto mutável]] ou seja, p====odemos fazer mais coisas com esse tipo além de acessar valores, como um CRUD.

```table-of-contents
```


--------
### Iniciar lista
Para **inicializar** uma lista, você pode declarar uma variável com o tipo ~={orange}list=~ ou apenas "~={orange}[]=~".
```python
lista = list()
# OU
lista = []
```
Nesse caso, estamos criando ~={green}listas vazias=~.

Podemos criar ~={green}listas com valores já atribuídos=~, onde poderia conter diversos tipos de dados juntos, dessa forma: 
```python
lista = [123, 'Daniel Canto', True, 1.80, []]
```
Nesse caso, nós temos uma lista com 5 itens.
Podemos também adicionar uma outra lista dentro dessa lista, caso seja necessário.

---------
#### Acessando elementos da lista
Para acessarmos os elementos de uma lista, podemos fazer dessa simples forma:
```python
lista = [123, 'Daniel Canto', True, 1.80, []]

print("Nome: ", lista[2])
# Nome: Daniel Canto
```
Vale ressaltar, que o ~={yellow}índice dos elementos de uma lista começa em 0.=~

Com isso, podemos também ~={green}alterar o valor de um índice =~de uma lista, dessa forma:
```Python
lista[2] = 'Mariana Gomes'
```

-----
### Funcionalidades da lista
Por ser um tipo mutável, a lista tem algumas funções a mais, que eu irei abordar aqui:

###### Delete - ~={orange}del=~ (Qualquer posição da lista)
Podemos apagar o valor e o índice de uma lista em qualquer parte, usando a função ~={orange}del=~, dessa forma:
```python
lista = [10, 20, 30, 40]
lista[2] = 300 # Alterando o valor de 30 para 300
del lista[2] # Estamos apagando o índice 2, a lista será reorganizada
print(lista) # Podemos ver que o 300 e nem o 30 existe
print(lista[2]) # Podemos ver que o novo índice 2 é o 40
```
~={red}OBS: =~ Apesar do Python fornecer essa possibilidade, seu uso não é recomendado, pois se a lista for muito extensa, reorganizar a lista custará muito processamento. Nesse caso, o ideal seria retirar elementos de umas das pontas da lista, aqui já entra o conceito de ~={pink}fila=~ e ~={pink}pilha=~.

###### Delete - ~={orange}pop()=~ (Apenas último da lista)
Ao contrário do ~={orange}del=~, o ~={orange}pop=~ sempre apagará o último índice da lista.
```Python
lista.pop()
```
Seu uso é mais recomendado que o ~={orange}del=~.

Você pode ~={green}pegar o valor removido=~ no mesmo instante com o ~={orange}pop=~, dessa forma:
```Python
valor_removido = lista.pop()
```

Apesar disso, o ~={green}~={orange}pop=~=~ também é capaz de ~={green}deletar um registro pelo índice=~, dessa forma:
```Python
lista.pop(2)
```
~={red}OBS: =~ Ele segue a mesma ideia do ~={orange}del=~.

##### Append (Adiciona itens ao fim da lista)
Podemos ~={green}adicionar novos índices=~ ~={green}no final=~ uma lista, através do método ~={orange}append=~.
```Python
lista = []

lista.append(10)
lista.append(20)
lista.append(30)
lista.append(40)
```
Dessa forma um novo índice com esses valores é adicionado à lista. No entanto, sempre no final dela.

##### Insert (Adiciona itens em um índice da lista)
Podemos também adicionar ~={green}novos índices em qualquer ponto da nossa lista=~. Esse método precisa de 2 argumentos, onde o primeiro é o índice e o segundo é o valor.
```Python
lista.insert(2, 300)
```
Dessa forma, o valor 300 foi adicionado ao índice 2. Vale ressaltar, que o valor antigo do índice 2 foi reorganizado para o índice 3 e assim por diante.

##### Clear
Ele simplesmente limpa toda a lista.
```Python
lista.clear()
```

###### Concatenar listas usando ~={orange}+=~ e ~={orange}extend=~
Podemos concatenar uma lista usando o ~={orange}+=~, fazemos dessa forma:
```Python
lista_a = [1, 2 , 3]
lista_b = [4, 5,  6]
lista_c = lista_a + lista_b
# Resultado : [1, 2, 3, 4, 5, 6]
```

Agora, para concatenar listas usando o método extend, fazemos da seguinte forma:
```Python
lista_a = [1, 2 , 3]
lista_b = [4, 5,  6]

lista_a.extend(lista_b)
# Resultado: [1, 2, 3, 4, 5, 6]
```
Como podemos ver, com o uso do extend, não foi possível usar uma variável, pois o método ~={red}extend alterou a lista A=~, e não apenas "copiou"seu valores
Com isso, é bom ~={red}tomar cuidado para não modificar indevidamente uma lista=~.

----
### Usando listas com estruturas de repetições
Para se utilizar uma lista com estrutura de repetições, normalmente usamos a [[Sintaxe Estruturas Básicas#Estrutura for|estrutura for]], dessa forma:
```python
numeros = [3, 9, 4, 1, 6, 7, 6, 13, 12]

for numero in numeros:
	print(numero)
```
No código acima, criamos uma lista de números inteiros, depois criamos um ~={orange}for=~, onde cada elemento da lista ~={orange}numeros=~ é inserido dentro da variável ~={orange}numero=~.
Como podemos perceber, isso é uma abstração do uso convencional dos arrays, como em C por exemplo, onde nós criamos uma estrutura de repetição com um índice, e acessamos cada elemento do array pelo índice.