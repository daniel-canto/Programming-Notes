#devops/github/comandos

Aqui estão listados alguns comandos do GitHub.

### Comandos principais
##### ~={orange}git add=~
Esse comando é utilizado para adicionar suas alterações para um "pacote". Podemos definir os arquivos usando caminhos ou simplesmente pegando todas as alterações com ~={orange}. =~

#### ~={orange}git status=~
Esse comando é usado para visualizar o status das modificações, onde ele exibe quais modificações não estão empacotadas.

#### ~={orange}git commit=~
Esse comando é usado para commitar o seu "pacote" (feito usado ~={orange}git add=~). Esse comando tem alguns parâmetros adicionais, como:
~={orange}-a=~: ele é usado para fazer o empacotamento de todas as alterações, sem usar o git add .
~={orange}-m=~: é usado para inserir o texto do seu commit (usado para explicar o commit)

#### ~={orange}git pull=~
Esse comando serve para puxar as atualizações do repositório do GitHub para o repositório local. Basicamente, sincroniza os dois repositórios.
Ele também possui alguns parâmetros, como:
~={orange}--rebase=~: ele é usado para manter um padrão no histórico de commits, se você alterou algo e antes de subir precisa sincronizar os repos, ele pode ser uma boa solução, pois ele pega o commit recente e coloca como pai do seu commit local. Muito útil para manter uma boa organização do histórico dos commits.

#### ~={orange}git stash=~
O ~={orange}git stash=~ é usado para salvar temporariamente alterações não commitadas. Ele é muito útil quando você precisa mudar de contexto, mas não está pronto para fazer um commit.
~={green}Um exemplo de uso, seria o mesmo do=~ ~={orange}git pull --rebase=~, onde ele poderia salvar suas alterações, possibilitando você atualizar seu repo local e depois trazer de novo suas alterações.
~={orange}git stash save "mensagem opcional"=~: usado para salvar suas alterações, seus parâmetros são:
~={orange}-u=~: serve para armazenar dados não empacotados também.

~={orange}git stash list=~: serve para verificar as stashs salvas.

~={orange}git stash apply stash@{n}=~: ele volta suas alterações para o código, mas mantém a stash na lista. (O 'n' seria a stash específica.)

~={orange}git stash pop stash@{n}=~: ele volta suas alterações para o código, mas retira a stash da lista.



