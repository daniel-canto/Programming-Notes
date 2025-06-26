#backend/python/estrutura_de_dados_python/dicionarios 

Ele é uma estrutura de dados do Python que armazena pares de chave-valor. Ou seja, ele permite que você associe uma chave (identificador único) a um valor correspondente.
Assim como a lista, o dicionário é um [[Tipos Mutáveis e Imutáveis#Objetos Mutáveis|objeto mutável]]. 
Normalmente, usamos dicionários para ~={green}representar coisas da vida real com suas características=~, como pessoa, pedidos, produtos e etc.
Além disso, essa estrutura é extremamente útil para APIs, pois sua estrutura se assemelha muito ao ~={green}JSON=~, tornando o trabalho com esse formato de dados mais simples.

```table-of-contents
```

----
### Como criar um dicionário?
Para simplesmente ~={green}inicializar =~um dicionário, podemos usar o ```dicionario = dict() ```.


Para~={green} criar um dicionário com dados=~, podemos fazer da seguinte forma:
```python
dicionario = {
	"nome": "Daniel",
	"idade": 19,
	"profissao": "Desenvolvedor de Software"
}
```
O dicionário simples sempre é criado utilizando chaves.

-----
### Como acessar valores do meu dicionário?
Para acessar seus valores, podemos fazer da seguinte forma (usarei o exemplo acima para demonstrar):
```python
print(dicionario["nome"]) # Aqui mostra o valor de uma chave, no caso Daniel
print(dicionario) # Aqui mostra todo o dicionário
```

----
### O que é uma lista de dicionários
Além dos dicionários simples, podemos criar uma lista de dicionários. Isso é útil, pois você pode guardar informações de diferentes pessoas na mesma estrutura, por exemplo:
```python
dicionario = {
	"nome": "Daniel",
	"idade": 19,
	"profissao": "Desenvolvedor de Software",
	"altura": 1.8,
	"enderecos": [
		{"rua": "Rua 1", "numero": 120, "cidade": "cidade 1"},
		{"rua": "Rua 2", "numero": 240, "cidade": "cidade 2"}
	],
}

print(dicionario["enderecos"]) # Aqui mostra os dois endereços

```
No código acima, eu fiz um dicionário para armazenar o registro de apenas uma pessoa, depois fiz uma lista de dicionários para armazenar mais de um endereço dessa pessoa.

----
### Funções do dicionário
##### Deletando chaves do dicionário usando ~={orange}del=~
Para excluirmos uma chave de um dicionário, podemos usar o comando ~={orange}del=~:
```Python
del dicionario["profissao"] 
```
O código acima ~={green}deleta a chave "profissão" do dicionário=~.

##### Adicionando valores para as chaves usando atribuição
Para adicionar valores nas chaves, podemos apenas usar o operador de atribuição na chave correspondente.
```Python
dicionario["profissao"] = "Desenvolvedor Web Backend"
```

##### Como verificar se uma chave existe no dicionário?
Para verificar se uma chave existe, podemos usar o método ~={orange}get=~, dessa forma:
```python
if dicionario.get("profissao"):
	print(dicionario["profissao"])
```
~={green}O método get pega o valor da chave, porém se ela não existir, ela retorna None ao invés de uma exception.=~ 
Dependendo do contexto, pode ser uma boa prática buscar valores de um dicionário usando esse método, pois evita interrupções no programa.
E para curiosidade, por padrão esse método é assim:
```Python
print(dicionario.get("profissao", None))
```
Onde após a vírgula, ele retorna um valor especificado (que por padrão desse método, é None, mas poderia ser 123 por exemplo, dessa forma ao invés de None, o retorno seria 123)
```Python
if dicionario.get("profissao"):
	print(dicionario["profissao"])
else:
	print(dicionario.get("profissao", 123))
	print("Chave inexistente.")
```

----
### Acessando valores do dicionário com estruturas de repetições
O dicionário em si não é iterável, no entanto o Python consegue fazer essa iteração através de métodos.

##### Como acessar as chaves do dicionário?
Para iteramos sobre todas as chaves do dicionário, podemos fazer da seguinte forma:
```python
dicionario = {
	"nome": "Daniel",
	"idade": 19,
	"profissao": "Desenvolvedor de Software",
	"altura": 1.8,
	"enderecos": [
		{"rua": "Rua 1", "numero": 120, "cidade": "cidade 1"},
		{"rua": "Rua 2", "numero": 240, "cidade": "cidade 2"}
	],
}

for chave in dicionario:
	print(chave)


```
No caso do código acima, estamos ~={green}pegando apenas o nome das chaves, e não o seu valor em si.=~ 

##### Como acessar os valores das chaves do dicionário?
Se quisermos apenas pegar os valores contidos nas chaves, podemos fazer da seguinte forma:
```python
dicionario = {
	"nome": "Daniel",
	"idade": 19,
	"profissao": "Desenvolvedor de Software",
	"altura": 1.8,
	"enderecos": [
		{"rua": "Rua 1", "numero": 120, "cidade": "cidade 1"},
		{"rua": "Rua 2", "numero": 240, "cidade": "cidade 2"}
	],
}

for chave in dicionario:
	print(dicionario[chave])
```
No código acima, estamos pegando apenas os valores.

Se quisermos montar o nosso dicionário com chave e valor, podemos fazer o seguinte:
```python
dicionario = {
	"nome": "Daniel",
	"idade": 19,
	"profissao": "Desenvolvedor de Software",
	"altura": 1.8,
	"enderecos": [
		{"rua": "Rua 1", "numero": 120, "cidade": "cidade 1"},
		{"rua": "Rua 2", "numero": 240, "cidade": "cidade 2"}
	],
}

for chave in dicionario:
	print(chave, "=", dicionario[chave])

```
