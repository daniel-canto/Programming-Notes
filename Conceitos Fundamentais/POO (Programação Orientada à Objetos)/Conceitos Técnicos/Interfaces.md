#conceitos_fundamentais/poo/conceitos_tecnicos/interfaces 

```table-of-contents
```
### O que é?
As interfaces seriam como uma lista de serviços fornecidos por um componente. É o contato com o mundo exterior, que define o que pode ser feito com um objeto dessa classe.
Exemplificando, elas funcionam como um contrato, onde ~={green}elas definem um conjunto de métodos (assinaturas) que uma classe deve obrigatoriamente implementar se quiser "assinar" essa interface (contrato)=~.
~={green}Esse conceito é muito atrelado ao conceito de [[Encapsulamento]], pois as interfaces facilitam a comunicação da lógica externa com a lógica interna de uma classe=~.
Vale ressaltar, que ao desenvolver uma interface para uma classe, essa classe deve ter seus atributos privados ou protegidos, mas os métodos podem ser públicos.
Abaixo, está um exemplo em UML de uma interface que implementa uma classe, nesse caso, o único diferencial fora do comum seria os métodos getter e setter estarem privados, normalmente são públicos. 
* Imagem:
	![[Pasted image 20250422094209.png]]

----
### Interface em código
Agora, vou demonstrar a implementação dessa interface utilizando algoritmos.
* Exemplo:
	**Criando uma interface com métodos abstratos: **
	```python
iinterface Controlador
"# Métodos abstratos
		 publico abstrato Metodo ligar()
		 publico abstrato Metodo desligar()
		 publico abstrato Metodo abrirMenu()
		 publico abstrato Metodo fecharMenu()
		 publico abstrato Metodo maisVolume()
		 publico abstrato Metodo menosVolume()
		 publico abstrato Metodo ligarMudo()
		 publico abstrato Metodo desligarMudo()
		 publico abstrato Metodo play()
		 publico abstrato Metodo pause()
 FimInterface

```

	**Criando a classe:**
	```python
cclasse ControleRemoto implementa Controlador
/# Atributos
	 privado inteiro volume
	 privado logico ligado
	 privado logico tocando
	
	# Métodos especiais
	 publico Metodo Construtor()
			 volume = 50
			 ligado = falso
			 tocando = falso
	 FimMetodo
	
	 privado Metodo getVolume()
			 retorne volume
	 FimMetodo
	 privado Metodo getLigado()
			 retorne ligado
	 FimMetodo
	 pprivado Metodo getTocando()
			 retorne tocando
	 FimMetodo
	
	 privado Metodo setVolume(v: Inteiro)
		     volume = v
	 FimMetodo
	 privado Metodo setLigado(l: logico)
			 ligado = l
	 FimMetodo
	 privado Metodo setTocando(t: logico)
			 tocando = t
	 FimMetodo


	# Sobrescrevendo Métodos
  publico Metodo ligar()
	(...)
	 FimMetodo
	publico Metodo desligar()
	(...)
	FimMetodo
	publico Metodo abrirMenu()
	(...)
	FimMetodo
	publico Metodo fecharMenu()
	(...)
	FimMetodo
	publico Metodo maisVolume()
	(...)
	FimMetodo
	publico Metodo menosVolume()
	(...)
	FimMetodo
	publico Metodo ligarMudo()
	(...)
	FimMetodo
	publico Metodo desligarMudo()
	(...)
	FimMetodo
	publico Metodo play()
	(...)
	FimMetodo
	publico Metodo pause()
	(...)
	FimMetodo

 FimClase

```

Vale ressaltar que ~={green}**quando você chama um método de uma interface, ele só será executado para o objeto específico da classe que você instanciou**,=~ não para todas as classes que implementam aquela interface.

----
### Características
* **Contrato de métodos**: uma interface declara métodos, mas não implementa nenhum deles, esse é o papel das classes, onde elas fornecem o código desses métodos.
* **Sem atributos de instância**: elas geralmente não possuem atributos de instância (variáveis que guardam estado), apenas constantes, se necessário.
* **Não podem ser instanciadas**: você não pode criar um objeto diretamente de uma interface, ela serve apenas como base para outras classes.
* **Implementação múltipla**: uma classe pode implementar várias interfaces ao mesmo tempo, resolvendo limitações como herança múltipla.
* **Abstração**: elas ajudam a separar a definição do que um objeto vai fazer (a interface) da forma como ele faz (a implementação).

----
### Qual seu objetivo?
* **Padronizar**: garantem que diferentes classes ofereçam os mesmos métodos, mesmo que a implementação interna seja diferente.
* **[[Polimorfismo]]**: permitem tratar objetos de diferentes classes de maneira uniforme, se eles implementarem a mesma interface.
* **Baixo acoplamento**: facilitam a troca de implementações sem alterar o código que usa a interface, tornando o sistema mais flexível e fácil de manter.