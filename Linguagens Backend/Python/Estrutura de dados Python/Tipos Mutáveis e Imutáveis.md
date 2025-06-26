#backend/python/estrutura_de_dados_python/tipos_mutaveis_e_imutaveis 

Em Python, a distinção entre objetos mutáveis e imutáveis é fundamental para entender como o gerenciamento de memória dessa linguagem funciona.

-----
#### Objetos Mutáveis
Os objetos mutáveis são objetos que seu estado interno pode ser alterado mesmo após sua criação. Ou seja, você pode modificar o conteúdo de um objeto sem criar um novo na memória.
No caso das [[Listas (Arrays)]] por exemplo, você pode adicionar, remover ou alterar elementos diretamente, por exemplo:
```Python
lista = [1, 2, 3]
lista[0] = 10  # Modifica o primeiro elemento
lista.append(4)  # Adiciona um elemento
print(lista)  # Saída: [10, 2, 3, 4]
```

Além das listas, outros tipos de dados possuem essa característica, como o [[Dicionários]] e o [[Conjuntos (sets)]].

##### Referências em objetos mutáveis
Quando você atribui uma lista à uma nova variável, ambas referenciam o mesmo objeto na memória. Ou seja, se alterar uma delas, a outra é afetada, exemplo:
```Python
lista1 = [1, 2, 3]
lista2 = lista1
lista2[0] = 100
print(lista1)  # Saída: [100, 2, 3]
```

Alguns objetos que seguem esse princípio:
* Listas
* Dicionários
* Conjuntos não congelados (set)
* Bytearray

-------
#### Objetos Imutáveis
Os objetos imutáveis não podem ser alterados após a criação. Qualquer "modificação" cria um novo objeto na memória.
Alguns objetos que seguem esse princípio são:
- Inteiros
- Float
- Strings
- [[Tuplas]]
- Conjuntos **(congelados,  frozenset)**
- Bytes
- Valores booleanos