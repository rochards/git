# Comandos de Git

### Controle de versionamento
Sistemas de Controle de Versionamento, em inglês *Version Control System* (VCS), são ferramentas que auxiliam o time de desenvolvimento a gerenciar mudanças no código ao longo do tempo. [1]

### GIT
**Git**, em suma, é um Sistema Distribuído de Controle de Versionamento, ou *Distributed VCS* (DVCS), uma vez que todo o conteúdo de um repositório remoto é completamente copiado para a máquina de cada contribuidor/desenvolvedor. [1]
O projeto é *open source* e foi desenvolvido originalmente em 2005 por Linus Torvalds, o famoso criado do kernel do Linux. [2]


### Principais comandos

Os comandos serão executados em algum terminal. Caso esteja em um sistema operacional Windows, recomendo a utilização do **Git Bash**.

* `git clone url-repositorio`: clona um repositório
  * Ex. `$ git clone https://github.com/freeCodeCamp/freeCodeCamp.git`

* `git status`: verifica o status do repositório
  * Ex. `$ git status`  
  ![Git status](images/git-status.png)

* `git add nome-arquivo`: adiciona o arquivo especificado
  * Ex. `$ git add README.md`

* `git add .`: adiciona todos os arquivos a partir do diretório atual.  
  Considere os diretórios abaixo e que todos os arquivos foram alterados  
  ![Arvore de diretorios](images/git-add-dot.png)
  * Ex1. Se estamos em **Git**, `$ git add .` então adiciona todos os arquivos;
  * Ex2. Se estamos em **Git/src**, `$ git add .` então só adiciona _**index.css**_ e _**index.css**_.
* `git commit -m "sua mensagem"`: comita as mudanças no repositório, antes adicionadas com um `git add`, com uma mensagem  
  Considerando que modificamos um arquivo **README.md** e já fizemos `git add README.md`. Quando executamos um `git status` é mostrado que o arquivo em questão está pronto para ser commitado
  ![Exemplo de commit](images/git-commit-1.png)
  * Ex. `git commit -m "Atualiza README.md"`

### Referências
[1] - https://www.atlassian.com/git/tutorials/what-is-version-control \
[2] - https://www.atlassian.com/git/tutorials/what-is-git
