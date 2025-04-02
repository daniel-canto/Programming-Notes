#backend/python/estrutura_de_dados/conjuntos

Os conjuntos são os mesmos conjuntos que aprendemos na escola, a teoria dos conjuntos.

Os sets em Python são [[Tipos Mutáveis e Imutáveis#Objetos Mutáveis|objetos mutáveis]], porém ~={green}seus itens são obrigatoriamente [[Tipos Mutáveis e Imutáveis#Objetos Imutáveis|tipos mutáveis]]=~.
Aqui estão suas principais características:
* Seus valores sempre serão únicos
* Não aceitam valores mutáveis.
* Não tem indexes (um dado específico não pode ser acessado diretamente).
* Não garantem ordem.
* São iteráveis (for, in, not in).

```table-of-contents
```

----
### Como inicializar um conjunto?
Para inicializarmos um conjunto, podemos usar a sua classe:
```python
conjunto = set()
```

Ou podemos fazer da seguinte forma:
```python
conjunto = {1, 2, 3}
```
Apesar dele lembrar um dicionário, repare que ele ~={green}não possuí chaves.=~

~={green}Se nós passarmos uma string dentro da classe=~ ~={orange}set()=~ dessa forma, ele irá ~={green}iterar sobre cada caractere da string.=~
```python
conjunto = set('Daniel')
print(conjunto) # Saída: {'D', 'i', 'a', 'e', 'l', 'n'}
```

Porém, ~={green}se inicializarmos nosso conjunto com chaves,=~ ele~={green} pega todo o conteúdo da string:=~
```python
conjunto = {'Daniel', 1, 2, 3}
print(conjunto) # Saída: {1, 2, 3, 'Daniel'}
```

----
### Métodos do set
Temos alguns métodos para manipular um set.

##### Adicionando novos itens
Para adicionar itens, podemos simplesmente usar o método ~={orange}add()=~.
```python
conjunto.add("Daniel")
conjunto.add(1)
```
Porém, ele não garante a ordem e ~={orange}~={green}adiciona apenas um item=~=~.

Para~={green} adicionar mais de um item=~, devemos usar o ~={orange}update()=~.
```python
conjunto.update(("Isabela", 1, 2, 3, 4))
```
Precisamos dos dois parênteses para indicar que ele é iterativo e assim armazenar tudo corretamente.

Se fizermos dessa forma:
```python
conjunto.update("Isabela")
```
Cada caractere será salvo no conjunto, e não toda a string.

##### Limpando o set
Para limpar o set, basta usar o método ~={orange}clear()=~.
```python
conjunto.clear()
```

##### Eliminando um valor
Podemos eliminar apenas um valor, utilizando o método ~={orange}discard()=~. Como os itens são tipos mutáveis e não temos índices no set, nós podemos simplesmente~={green} excluir pelo valor=~ mesmo, dessa forma:
```python
conjunto.add("Isabela")
conjunto.discard("Isabela")
```

----
### Operadores úteis
Como eu disse no começo, o conjunto do python é baseado na teoria dos conjuntos da matemática. Portanto, temos os seguintes operadores.

##### União (Union) - |
Ele une dois conjuntos.
```python
c1 = {1, 2, 3}
c2 = {2, 3, 4}
s3 = c1 | c2
print(s3) # Saída: {1, 2, 3, 4}
```

##### Intersecção (Intersection) - &
Ele pega os itens presentes em ambos os conjuntos.
```python
c1 = {1, 2, 3}
c2 = {2, 3, 4}
s3 = c1 & c2
print(s3) # Saída: {2, 3}
```

##### Diferença - 
Pega os itens presentes apenas no set da esquerda que não estejam no set da direita.
```python
c1 = {1, 2, 3}
c2 = {2, 3, 4}
s3 = c1 - c2
print(s3) # Saída: {1}
```

##### Diferença similar - ^
Pega os itens que não estão em ambos sets.
```python
c1 = {1, 2, 3}
c2 = {2, 3, 4}
s3 = c1 ^ c2
print(s3) # Saída: {1, 4}
```

 