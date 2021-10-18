# Comandos de Git

### Controle de versionamento
Sistemas de Controle de Versionamento, em inglês *Version Control System* (VCS), são ferramentas que auxiliam o time de desenvolvimento a gerenciar mudanças no código ao longo do tempo. [1]

### GIT
**Git**, em suma, é um Sistema Distribuído de Controle de Versionamento, ou *Distributed VCS* (DVCS), uma vez que todo o conteúdo de um repositório remoto é completamente copiado para a máquina de cada contribuidor/desenvolvedor. [1]
O projeto é *open source* e foi desenvolvido originalmente em 2005 por Linus Torvalds, o famoso criado do kernel do Linux. [2]

Antes de começarmos, aprenda a instalar o [Git](https://www.atlassian.com/br/git/tutorials/install-git) de acordo com seu Sistema Operacional.

### Principais comandos

OBS1.: Os comandos são iniciados com o símbolo `$` apenas para indicar que estão sendo executados no terminal, não fazendo parte da instrução.

OBS2.: Caso esteja em um sistema operacional Windows, recomendo a utilização do **Git Bash**.

* `git init`: inicializa um novo repositório Git em sua máquina.
  * Ex. Se executamos `$ git init` em **Documentos/my-project**, então **my-project** agora é um repositório git. 

* `git clone <url-repositorio>`: clona um repositório:
  * Ex. `$ git clone https://github.com/freeCodeCamp/freeCodeCamp.git`

* `git status`: verifica o status do repositório:
  * Ex. `$ git status`  
  ![Git status](images/git-status.png)

* `git log`: exibe todo o histório de _commits_;

* `git log -n <limit>`: limita o número de _commits_ a serem exibidos:
  * Ex. `$ git log -n 3` vai exibir apenas 3 _commits_

* `git log --oneline`: condensa a exibição dos _commits_ em uma linha

* `git add <nome-arquivo>`: adiciona o arquivo especificado:
  * Ex. `$ git add README.md`

* `git add .`: adiciona todos os arquivos a partir do diretório atual.  
  Considere os diretórios abaixo e que todos os arquivos foram alterados  
  ![Arvore de diretorios](images/git-add-dot.png)
  * Ex1. Se estamos em **Git**, `$ git add .` então adiciona todos os arquivos;
  * Ex2. Se estamos em **Git/src**, `$ git add .` então só adiciona _**index.css**_ e _**index.css**_

* `git commit -m "sua mensagem"`: comita as mudanças no repositório, antes adicionadas por um `git add`, com uma mensagem.  
  Considerando que modificamos um arquivo **README.md** e já fizemos `git add README.md`. Quando executamos um `git status` é mostrado que o arquivo em questão está pronto para ser comitado
  ![Exemplo de commit](images/git-commit-1.png)
  * Ex. `git commit -m "Atualiza README.md"`

* `git commit -m "Titulo do commit" -m "Mais detathes do commit"`: uma variação do comando para você detalhar melhor suas alterações. Você pode inserir quantos `-m` desejar, ao final cada mensagem aparecerá em um parágrafo diferente;

* `git commit`: executado dessa forma o Git abre um editor de texto para nos dar mais liberdade ao escrever nossos commits. Você pode saber mais procurando na [documentação](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration) por _core.editor_;

* `git commit -v`: permite que você veja, no editor de texto _default_, as mudanças que serão adicionadas neste commit.
  * Considere que executamos um `$ git add .` para adicionar as modificações no arquivo **README.md** e em seguida `$ git commit -v`. A figura abaixo mostra o resultado no editor _default_:
  ![Git commit -v](images/git-commit-v-modified.jpg)
* `git branch`: lista os _branches_ existentes no repositório;

* `git branch -r`: lista os _branches_ presentes no repositório remoto;

* `git branch -a`: lista todos os _branches_, remotos e locais;

* `git branch -d <nome-da-branch>`: deleta o _branch_ especificado;

* `git branch -m <novo-nome>`: renomeia o _branch_ atual com o nome especificado;

* `git remote -v`: lista as referências para repositórios remotos e respectivas urls presentes no seu repositório local.  
  Considerando que o comando acima foi executado, na imagem abaixo é mostrada uma referência chamada **origin** para um repositório remoto:  
  ![Exemplo remote -v](images/git-remote-v.png)

* `git remote add <nome-repositorio-remoto> <url>`: associa seu repositório local a um remoto, cujo `nome-repositorio-remoto` é de sua escolha:
  * Ex.: `$ git remote add origin https://github.com/rochards/new-project.git`. Por convenção, chamamos nossa referência para o repositório remoto de **origin**.

* `git remote rename <nome-atual> <novo-nome>`: comando para renomear o nome da referência para o repositório remoto:
  * Ex. `$ git remote rename origin origin-git`

* `git remote remove <nome-repositorio-remoto>`: exclui a referência, que existe na sua máquina, para o repositório remoto:
  * Ex. `$ git remote remove origin`

* `git checkout -b <nome-novo-branch>`: cria um novo _branch_ e já o seleciona como o atual:
  * Ex. `$ git checkout -b fix-bug` 

* `git checkout <hash-commit>`: visualiza as alterações do projeto até o _commit_ indicado. Esse comando é muito útil para você "andar" pelo histórico de modificações. O comando é seguro, pois não alterará o estado atual do seu projeto:
  * Ex.: `$ git checkout 9e101fd`. Supondo que antes do _checkout_ estávamos no _branch_ `develop`, caso queira voltar ao estado atual do _branch_ basta executar `git checkout develop`.

* `git fetch`: baixa arquivos, commits e referências de um repositório remoto. Por padrão as buscas são feitas em **origin**. Esse comando é seguro, porque nada será alterado em seus *branchs* locais;
  * Ex1.
    * Você gostaria de verificar se houveram modificações no *branch* remoto e antes de fazer o merge gostaria de olhar as alterações -> `$ git fetch`
    ![Exemplo git fetch](images/git-fetch.png)
    * Algumas *features* foram adicionadas no repositório remoto e podemos confirmar -> `$ git status` 
    ![Exemplo git status](images/git-status-2.png)
    * Podemos verificar a diferença entre o repositório local e o remoto utilizando os dois *hashs* apresentados na figura anterior -> `$ git diff d99196f..d98661f`
    ![Exemplo git diff](images/git-diff.png)
    * Agora, para trazer as alterações para nosso repositório local basta executar um *merge* com o *hash* do *commit* remoto -> `$ git merge d98661f`  
    ![Exemplo git merge](images/git-merge.png)
  
  * **Obs.:** fazendo um `$ git pull` o *fetch* e *merge* são feitos automaticamente.

* `git fetch <remote> <nome-do-branch>`: busca apenas as alterações no _branch_ especificado do repositório remoto;

* `git revert HEAD`: desfaz as alterações do último _commit_. O Git adiciona um novo _commit_ que desfaz todas as alterações do commit anterior:
  * Ex1: 
    * Verifiquemos os _commit_ existentes com `$ git log --oneline`  
    ![Exemplo git revert](images/git-revert-1.png)
    * Executando `$ git revert HEAD`  
    ![Exemplo git revert](images/git-revert-2.png)
  
  * Ex2: `git revert HEAD~1` reverteria as modificações do primeiro _commit_ anterior à HEAD;
  * Ex3: `git revert HEAD~2` reverteria as modificações do segundo _commit_ anterior à HEAD e assim por diante.
  
  **Obs**.: reverter modificações anteriores à HEAD pode requerer uma ação manual para resolver conflitos.

* `git revert --abort`: cancela tentativa de reverter o _commit_. Pode ser utilizado quando o comando de _git revert_ resultou em conflitos.
  
### Referências
[1] - https://www.atlassian.com/git/tutorials/what-is-version-control \
[2] - https://www.atlassian.com/git/tutorials/what-is-git
