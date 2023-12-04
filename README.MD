# Tutorial de Git e Github na prática

# Intalação do git
* [Link com downloads](https://git-scm.com/downloads)

## Versionamento local do projeto 
* Acesse a pasta na qual o projeto está armazenado
* Clique com o botão direito do mouse e selecione **Open Git Bash here**
* Digite `git init` para inicializar o repositório
  
  Será criada uma pasta chamada `.git`, **não** a apague
* Digite `git add .` para colocar os arquivos do projeto na **área de staging**
<img src="https://i1.wp.com/www.markus-gattol.name/misc/mm/si/content/git_git_add.png">

* Digite `git commit -m "primeira versão do projeto"` para versionar **localmente** o projeto
* Digite `git branch -M "main"` para renomear a branch principal de `master` para `main`
  
## Criação de um repositório remoto no Github
* Acesse a sua conta do Github e clique em `New` para criar um novo repositório

    Coloque um nome para o respositório e preencha as informações do projeto, como a descrição
* Para enviar o commit do repositório local (isto é, em sua máquina) para um repositório na
    plataforma do Github, digite por linha de comando `git remote add origin <link do repositório>`

    `origin` é o nome utilizado para referenciar o link do repositório remoto

* Dessa forma, o repositório local já está vinculado ao repositório remoto do Github, entretanto a versão (isto é, o commit) não sobe automaticamente, por isso é necessário digitar:**`git push -u origin main`**
*Por fim, recarregue a página do Github e verifique se o projeto foi versionado **remotamente**

## E quando o projeto for alterado?

* Ao editar um arquivo já ou mesmo criar um novo arquivo que não existia   na versão anterior, **NÃO** é necessário inicializar novamente o Git por meio do comando `git init`, sendo assim execute **APENAS** os seguintes comandos em ordem:
    `git add .`

    `git status` para verificar os arquivos que esteja aguardando na staging area

    `git commit -m "<escrevar uma mensagem detalhando o que foi alterando>"`

    `git push`

    como é possível notar, também **NÃO** é necessário renomear mais um vez a branch (pois ela já estará renoameada com `main`), além disso, o link do repositório remoto já estará armazenado, por isso o comando `git remote add origin <link do repositório>` só é utilizando uma única vez 

* No Github será possível verificar todas as versões enviadas clicando em `commits`, de modo que todas as alterações feitas estarão demonstradas

    O verde verde `+` representa o que foi adicionado/modificado ao versionamento, enquanto sinal vermelho `-` representa o que foi excluído de uma versão para outra


## Branch

* Até então, todos os versionamento ocorreram na **ramificação principal (branch `main`)**

* Para criar uma nova branch, isto é, uma nova linha cronológica adicionar/alternativa à principal que possa posteriormente se juntar à `main`, digite `git checkout -b <nome da nova branch>`, assim o terminal Git sairá da branch `main`, criará um nova com o nome que desejar e entrará nela, por exemplo: `git checkout -b novoBotao`

* Com uma nova branch criada, ultilizar os comando já explicado:
     `git add .`

    `git status` 

    `git commit -m "<escrevar uma mensagem detalhando o que foi alterando>"`

    `git push -u origin novoBotao`

* No Github, as branches aparecerão assim:

    <img src="img/imgBranch.PNG">

* Se necessário retonar para branch `main` pelo terminal do Git, digite `git checkout main`

## merge

* Ao retornar para a branch `main`, digite `git merge <nome da nova branch>` (no exemplo acima, seria a branch chamada novoBotao), desse modo será  possivel **unificar a branch alternativa e a branch principal em uma só**

* Desse modo, tudo o que tinha de alteração na branch novoBotao (por exemplo) se juntará à branch `main`

* Para finalizar digite `git push origin main` e suba os arquivos para a branch principal do repositorio remoto

## Clone

* Para fazer o download de um repositório remoto, seu ou de outro usuário, há duas opções:
* 1ª opção: clicar no botão `Code` que se encontra no próprio Github e em seguida no botão `Download ZIP`, conforme a imagem abaixo
  
  <img src="./img/imgClone.PNG">

* 2ª opção: utilizando o mesmo link presente na imagem acima, abra o terminal e digite `git clone <link copiado do repositório remoto>`
**Observação**: é importante que ao clonar um repositório de sua própria conta no Github,
verifique qual branch no Github está como `default`, pois o **projeto clonado será aquele que se encontra na branch `default`**

## Pull

* E se o desenvolvedor, ao digitar novos códigos em seu computador de casa e enviá-los para o repositório remoto, perceber ao chegar no trabalho que o projeto na máquina do escritório está desatualizado?

* Para puxar **todas as alterações realizadas do repositório remoto (Github) para o seu repositório local**, digite `git pull`
