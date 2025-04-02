#backend/python/estrutura_de_dados/tuplas
Basicamente, a tupla é uma [[Listas (Arrays)|lista]] [[Tipos Mutáveis e Imutáveis#Objetos Imutáveis|imutável]], ou seja, seus valores não podem ser alterados.

Apesar disso, a tupla é mais rápida que a lista, por isso quando não precisamos alterar uma lista, é melhor usar uma tupla, por questões performáticas. 

----
### Como criar uma tupla?
Para criamos uma tupla com valores, é muito fácil, fazemos da seguinte forma:
```python
nomes = 'Daniel', 'Bruno', 'Viviane', 'Isabela', 'Mariana'

print(nomes)
```
Perceba que lembra muito quando criamos uma lista, porém não usamos os colchetes para isso.

Podemos também criar uma tupla utilizando parênteses, dessa forma: 
```python
nomes = ('Daniel', 'Bruno', 'Viviane', 'Isabela', 'Mariana')

print(nomes)
```
Inclusive, ao dar print em uma tupla, vemos que o retorno dela vem dentro de parênteses.

----
### Sobre atribuições em tuplas
Por ser um tipo imutável, não conseguimos fazer atribuições de nenhuma forma para essa estrutura de dados. Se tentarmos fazer uma atribuição igual fazemos à uma lista, uma exception 'TypeError' irá surgir.

### Conversão de tupla pra lista e vice-versa
Por serem estruturas iguais, com características diferentes, podemos converter essa estrutura, caso seja uma necessidade.

##### De lista para tupla:
```python
nomes = ['Daniel', 'Bruno', 'Viviane', 'Isabela', 'Mariana']
nomes = tuple(nomes)
print(nomes) # Saída: ('Daniel', 'Bruno', 'Viviane', 'Isabela', 'Mariana')
```

##### De tupla para lista:
```python
nomes = ('Daniel', 'Bruno', 'Viviane', 'Isabela', 'Mariana')
nomes = list(nomes)
print(nomes) # Saída: ['Daniel', 'Bruno', 'Viviane', 'Isabela', 'Mariana']
```

