#devops/github/dicas_e_boas_praticas/nao_usar_git_pull 
### Cenário do problema
Vamos supor que tenha duas pessoas trabalhando na mesma branch de um projeto, vamos chamá-las de Jonh e Mark.
Jonh estava fazendo uma correção de bug, enquanto Mark estava fazendo uma implementação de uma nova funcionalidade.
No entanto, Jonh subiu suas alterações primeiro, assim criando o seu commit, enquanto Mark subiu seu commit depois. 
O problema começa, quando o Mark vai tentar dar um novo commit, seu repositório local está desatualizado em relação ao GitHub, portanto o GitHub recusa seu commit e pede para ele atualizar antes, porém se o mark simplesmente utilizar o ~={orange}git pull=~, a organização dos commits ficará confusa, pois os dois commits ficarão lado a lado, gerando um novo commit acima herdando os dois abaixo, dessa forma:
![[Pasted image 20250324153449.png]]
Assim, dificultando o rastreamento de um determinado commit, gerando uma desorganização.

### Qual a forma de resolver esse problema?
Uma das formas de se resolver isso é salvando e retirando suas alterações, atualizando o repo local, voltando com as alterações e subindo para o GitHub.
Para isso, podemos usar o ~={orange}git stash=~, você pode consultas esse comando aqui: [[Comandos#~={orange}git stash=~]]
Dessa forma, seus commits ficam com um histórico organizado assim:
![[Pasted image 20250324153652.png]]


Outra forma seria simplesmente utilizar o ~={orange}git pull --rebase=~, onde ao invés dele deixar os dois commits "lado a lado", ele o deixa de forma linear, onde o commit não constado no repo local, irá seu tornar "pai" do seu commit, dessa forma:
**~={red}OBS:=~** Caso você tenha um ~={green}Merge Conflict=~ usando o ~={orange}git pull --rebase=~, você pode simplesmente ~={green}aplicar=~ o ~={orange}git rebase --abort=~.

Apesar disso tudo, o uso do ~={orange}git stash=~ pode ser mais recomendado, por evitar merge conflict.