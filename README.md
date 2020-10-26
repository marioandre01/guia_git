# Git e GitHub
 
Guia prático para iniciantes.
 
### Instalação
 
https://git-scm.com/download
 
Configurações iniciais
 
``` 
git config --global user.name "Seu_Nome_Aqui"
git config --global user.email "seuemail@exemplo.com"
``` 
 
O git precisa saber quem é o usuário antes de registrar os commits.
 
## Cenários de uso
 
- [x] Você deseja criar pontos na história da produção do seu projeto 
- `git init` // Inicia a linha do tempo;
- `git add nome_do_arquivo` // Adiciona mudanças para irem para a linha do tempo;
- `git commit -m "Uma mensagem para registar o que foi feito"` // Adiciona um ponto na linha do tempo;
 
- [x] Você deseja verificar mudanças feitas no seu projeto
- `git status` // Informa o estado das alterações do nosso projeto;
- `git log` // Visualiza os pontos na linha do tempo/commit;
 
 - `git show numero_do_commit` // Olhar os pontos na história. Para ver o número do commit utilizar `git log`. Vai mostrar o histórico de todos os commits feitos, cada commit tem um número o referenciando;
 
 - `git show` // Ver o último ponto na história - último commit feito;
 
 ---
 
- [x] Você começa uma nova funcionalidade no seu projeto, sem estragar o que já foi feito.
`git branch nome_da_branch`
`git checkout nome_da_branch`   

---
 
- [x] Você adiciona as novas funcionalidades ao seu projeto, em produção
`git checkout master`
`git merge nome_da_branch`   

---
 
- [x] Você quer deletar a branch da nova funcionalidade, depois de aplicar em seu projeto.
`git branch -D nome_da_branch`

---
 
- [x] Você quer colocar seu projeto na nuvem
Ir no seu github e criar um repositório, por boas práticas coloque o nome do repositório com o mesmo nome da pasta do projeto. Mas pode-se utilizar outro nome se quiser.
`git remote add origin https://github.com/nome_conta/nome_repositório.git`
 
`git remote -v` para ver os repositórios remotos do usuário.
 
`git push -u origin master` vai empurrar o repositório local para o repositório online. Como o push vai ser feito pela primeira vez é necessário criar a branch master no repositório online (-u origin master).
 
Vai se pedido o nome de usuário do git e a senha. Caso o github já esteja configurado com uma chave privada, o envio vai ser feito direto.
 
Na próxima vez que for fazer um push, só precisa digitar:
`git push`
pois a branch master já foi criada no repositório online
 
para não ter que ficar sempre digitando o nome de usuário e senha toda vez que fizer um push, fazer:
`git config credential.helper store`
 
com isso não é mais preciso colocar nome de usuário e senha, pois será usado as informações de usuário e senha da última vez.

---
 
- [x] Você vai pegar um projeto já iniciado, para trabalhar com o time
`git clone https://github.com/nome_usuario/nome_projeto.git`
 
Entrar na pasta
`cd nome_projeto`
 
Agora será criado um cenário de conflito
 
- [x] Você precisa resolver um conflito.
 
Primeiro criar uma branch nova e mudar para essa branch
`git checkout -b teste`
Esse é um comando curto que vai criar uma nova branch e já vai mudar para essa branch
 
Representa a mesma sequência de comandos
`git branch nome_da_branch`
`git checkout nome_da_branch`   
 
Ir em um arquivo dessa pasta e modificá-lo, ex: apagar uma linha
depois fazer 
`git status`
para confirmar a alteração
 
Fazer o commit da alteração, pode-se utilizar um comando curto
`git commit -am "mensagem para registrar o que foi feito"`
 
representa a mesma sequência de comandos
`git add nome_do_arquivo`
`git commit -m "Uma mensagem para registar o que foi feito"`
 
Voltar para a branch master
`git checkout master`
 
Ir na mesma linha que na branch teste foi apagada e inserir algum texto nela
arquivo package.json
 
`git add .`
`git commit -m "mensagem para registrar o que foi feito"`
 
unir as duas linhas do tempo, estando na branch master
`git merge teste`
 
Vai aparecer a mensagem de conflito
"Auto-merging package.json
CONFLICT (content): Merge conflict in package.json
Automatic merge failed; fix conflicts and then commit the result."
 
Usando o visual studio, ele vai mostrar algumas opções pelo programa, que são: aceitar a alteração da branch master, aceitar a alteração da branch teste, aceitar a alteração das duas branchs e comparar as mudanças. 
 
Será escolhido a primeira opção "aceitar a alteração da branch master"
 
salvar a alteração
 
fazendo um 
`git status`
 
vai mostrar que não ocorreu a merge, pois houve um conflito.
 
Com a escolha da opção "aceitar a alteração da branch master" e ja salva, então fazer:
 
`git commit -am "conflict resolved"`
 
confirmar se o conflito foi resolvido com
`git status`
`git log`
 
 
- [x] Antes de enviar o projeto, precisamos atualizar o projeto local.
Ir no repositório remoto e ir no README do projeto e fazer alguma alteração, ex: apagar algumas linhas
 
Antes de fazer um push para o repositório remoto fazer:
`git pull`
 
esse comando vai puxar atualizações que ocorreram no projeto na nuvem (repositório remoto)
 
Imagina que você está trabalhando com um time, algum colega seu alterou na máquina dele algum arquivo e enviou essa alteração (git push) para o repositório remoto. Quando ele enviou essa alteração para o repositório remoto, você precisa atualizar essas informações no seu projeto local, antes de enviar as suas alterações. Porque senão vai gerar conflitos, pois não sabe-se o que mudou ou deixou de mudar lá.
 
Feito o "git pull" pode-se fazer  o
`git push`
 
- [x] Você precisa voltar um arquivo para um determinado momento da linha do tempo
 
Deseja-se voltar uma alteração que foi feita em algum arquivo.
 
Que momento é esse?
 
com
`git log`
 
verifica-se qual momento se quer voltar, escolhido o momento anotar o número do commit escolhido
 
então fazer
`git checkout numero_do_commit -- nome_do_arquivo_a_voltar_a_alteração`
 
`git commit -am "mensagem para registrar o que foi feito"`
 
`git pull`
 
para ver se não teve nenhuma alteração no repositório remoto
 
então:
`git push`
 
 
- [x] Você precisa recuperar algo deletado. 
 
Deletar um arquivo do projeto
 
verificar com: 
`git status`
 
o git status vai mostrar que o arquivo foi deletado, mas ele não foi adicionado em um ponto na história. Como ele não foi adicionado em um ponto na história, para recupera-lo fazer
`git checkout -- nome_do_arquivo_excluído`
 
Como depois da palavra checkout não foi passado um número de commit (um ponto na história), será usado o ponto na história atual (último commit feito).
 
Vamos supor que o arquivo foi deletado e foi adicionado em um ponto da história
 
Deletar o arquivo
fazer
`git commit -am "delete LICENSE.md"`
 
se tentar fazer
`git checkout -- nome_do_arquivo_excluído`
 
Não vai funcionar, vai mostrar um erro, pois no último commit feito o arquivo não existe.
 
Para consegui recuperar o arquivo deve-se utilizar um ponto na história (numero do commit) anterior onde o arquivo existia.
 
Para isso fazer
`git checkout numero_do_commit -- nome_do_arquivo_excluído`
 
Desse modo para recuperar um arquivo deletado seja o tempo que for, é só usar um tempo na história que ele estava criado. 
 
## Resumo comandos
 
* `git init` // inicia a linha do tempo
* `git add` // adiciona ou atualiza mudanças para irem para a linha do tempo
* `git commit` //adiciona um ponto na linha do tempo
* `git log`  // visualiza os pontos na linha do tempo / commit
* `git status`  //informa o estado das alterações do nosso projeto
* `git show` // apresenta determinado ponto na história
* `git branch` //gerenciar novas linhas do tempo
* `git checkout` //manipula as linhas do tempo, seleciona a linha do tempo a ser usada
* `git merge` // unir linhas do tempo
* `git push` // envia alterações locais para o repositório remoto
* `git clone` // clonar um projeto / repositório
* `git pull`  // puxa do repositório remoto
 
Referência: [Como usar Git e Github na prática: Guia para iniciantes | Mayk Brito - Rocketseat](https://www.youtube.com/watch?v=2alg7MQ6_sI)

