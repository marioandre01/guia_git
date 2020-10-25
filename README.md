# Git e GitHub

Guia prático para inciantes.

### Instalação

https://git-scm.com/download

configurações iniciais

git config --global user.name "Seu_Nome_Aqui"
git config --global user.email "seuemail@exemplo.com"

o git precisa saber quem é o usuário antes de registrar os commits.

# Cenários

- [x] Você deseja criar pontos na história da produção do seu projeto (git init, git add, git commit -m "")
- [x] Você deseja verificar mudanças feitas no seu projeto (git status, git log)

olhar os pontos na história:
git show numero_do_commit

ver o último ponto na história
git show

- [x] Você começa uma nova funcionalidade no seu projreto, sem estragar o que já foi feito.
`git branch nome_da_branch`
`git checkout nome_da_branch`   

- [x] Você adiciona as novas funcionalidades ao seu projeto, em produção
`git checkout master`
`git merge nome_da_branch`   

- [x] Você quer deletar a branch da nova funcionalidade, depois de aplicar em seu projeto.
`git branch -D nome_da_branch`

- [x] Você quer colocar seu projeto na nuvem
Ir no seu github e criar um repositorio, por padrão coloque o nome do repositório com o mesmmo nome da pasta do projeto. Mas pode-se utilizar outro nome se quiser.
`git remote add origin https://github.com/nome_conta/nome_repositório.git`
`git remote -v` para ver os repositórios remotos do usuário.
`git push -u origin master` vai empurrar o repositório local para o repositório online. Como o push vai ser feito pela primeira vez é necessário criar a branch master no repositório online.

vai pedir o nome de usuário do git e a senha. Caso o github ja esteja configurado com uma chave privada, o envio vai ser feito direto.

- [x] Você vai pegar um projeto ja iniciado, para trabalhar com o time
- [x] Você precisa resolver um conflito.
- [x] Antes de enviar o projeto, precisamos atualizar o projeto local.

- [x] Você precisa voltar um arquivo para um determinado momento da linha do tempo
- [x] Você precisa recuperar algo deletado. 

* `git init` // inicia a linha do tempo
* `git add` // adiciona ou atualiza mudanças para irem para a linha do tempo
* `git commit` //adiciona um ponto na linha do tempo
* `git log`  // visualiza os pontos na linha do tempo / commit
* `git status`  //informa o estado das alterações do nosso projeto
* `git show` // apresenta determinado ponto na história
* `git branch` //gerenciar novas linhs do tempo
* `git checkout` //manipula as linhas do tempo
* `git merge` // unir linhas do tempo
* `git push` // envia alterações locais para o repositório remoto
* `git clone` // clonar um projeto / repositório
* `git pull`  // puxa do repositório remoto