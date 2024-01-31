# course-git-and-github


### Sumário de aprendizados:
1. [Download e Instalação do Git](#1-passo)
2. [Configuração do Git](#2-passo)
3. [Praticando](#praticando)
   - [Inicializando o Repositório](#inicializando-o-repositorio)
   - [Untracked ou Tracked](#untracked-ou-tracked)
   - [Primeiro Commit (Versões)](#primeiro-commit-versoes)
   - [Modificando um arquivo ja commitado](#modificando-um-arquivo-ja-commitado)
   - [Visualizando a Log (Todos Commits realizados)](#visualizando-a-log-todos-commits-realizados)
   - [Renomeando o último commit](#renomeando-o-ultimo-commit)
   - [Voltando a outros commits](#voltando-a-outros-commits)
   - [Renomeando arquivo](#renomeando-arquivo)
   - [Removendo arquivo](#removendo-arquivo)
- Branches:
   - [Consultando lista de branches](#consultando-lista-de-branches)
   - [Criando uma nova branch](#criando-uma-nova-branch)
   - [Navegando pelas branches](#navegando-pelas-branches)
   - [Removendo uma branch](#removendo-uma-branch)

### 1. Passo
Primeiro, começamos baixando o Git através do [Download Git](https://git-scm.com/downloads). Depois, realizamos a instalação padrão do programa.

#

### 2. Passo
Em seguida, configurei o Git com os seguintes comandos:

```bash
git config --global user.name "Nome do usuário"
```

```bash
git config --global user.email SeuEmail
```

```bash
git config --global init.defaultBranch main
```

Certifique-se de substituir "Nome do usuário" pelo seu nome de usuário, "SeuEmail" pelo seu endereço de e-mail e "main" pelo nome da branch padrão que deseja usar, se necessário.

#

### Praticando

- #### Inicializando o repositorio

    Antes de inicializar um repositório, precisamos acessar o caminho até a pasta atual que queremos inicializar. Para fazer isso:
    
    ```powershell
    cd local/da/sua/pasta
    ```

    Para verificar se estamos no local certo, basta executar o comando (dir). Esse comando mostrará os arquivos que estão dentro da pasta local. Isso nos permitirá confirmar se estamos no diretório desejado antes de prosseguir.

    ```powershell
    dir local/da/sua/pasta
    ```

    Depois de verificar o diretório desejado e confirmar que estamos no local certo, podemos inicializar o repositório com o seguinte comando. Isso permitirá que o Git comece a monitorar os arquivos:

    ```bash
    git init
    ```
    Agora, o Git está configurado para rastrear as mudanças nos arquivos nesta pasta.

#

- #### Untracked ou Tracked
    
    Após a inicialização do diretório, o Git começa a rastrear os arquivos no diretório. Precisamos fazer com que eles saiam do estado "Untracked" para "Tracked", o que significa que começaremos a criar versões para cada alteração feita nos arquivos.

    Isso é importante porque, quando os arquivos estão "Tracked", o Git pode monitorar e registrar todas as alterações, permitindo-nos controlar o histórico das versões do nosso projeto. Para começar a rastrear os arquivos, podemos usar o seguinte comando:
    
    ```bash
    git add nome-do-arquivo
    ```
    Substitua "nome-do-arquivo" pelo nome real do arquivo que deseja rastrear.

    Agora, ao usar o comando abaixo, podemos ver que aparecerá um "(new file)" em verde ao lado do nome do arquivo que acabamos de adicionar e, abaixo disso, uma lista em vermelho dos arquivos "Untracked":
    
    ```bash
    git status
    ```

    Caso tenha adicionado o arquivo errado é possivel retornar ele para "Untracked" / "Unstaged"

    ```bash
    git rm --cached nome-do-arquivo
    ```

#

- #### Primeiro Commit (Versoes)

    Agora que realizamos o `git add` para o arquivo que queremos criar uma versão e verificamos que ele ficou verde no `git status`, é hora de criar a nova versão usando o seguinte comando:

    ```bash
    git commit -m "[Tipo do commit]: Mensagem do commit"
    ```

    Substitua "Mensagem do commit" pela descrição breve do que foi feito neste commit. Esta mensagem ajuda a descrever as alterações feitas neste ponto da história do projeto. 

#

- #### Modificando um arquivo ja commitado

    Após fazer o primeiro commit de um arquivo, criamos sua primeira "versão". Quando fazemos uma alteração nesse arquivo, podemos observar no `git status` que ele aparecerá como "(modified)", ou seja, estaremos criando uma segunda versão desse arquivo.

    Lembrando que cada vez que fizermos uma alteração significativa, devemos seguir os passos novamente para adicionar, commitar e documentar essa mudança usando os comandos.

#

- #### Visualizando a log (Todos Commit's realizados)
    
    Agora, para visualizar todos os logs que foram registrados durante as modificações realizadas nos arquivos, podemos usar os comandos abaixos:
  
  ####

    Log's gerais:
    ```bash
    git log
    ```
  Log's mais otimizado:
  ```bash
    git log --oneline
    ```
  Log's mais detalhado:
  ```bash
    git log -p
    ```

    Estes comandos exibirá uma lista de todos os commits que foram feitos, incluindo detalhes como a data, o autor e a mensagem de cada commit. Isso nos permite rastrear o histórico completo do projeto e todas as alterações.
    
#

- #### Renomeando o ultimo commit.

    Se cometer um erro na mensagem do meu último commit e ainda não o enviou para o GitHub, pode fazer a alteração da seguinte forma:

    ```bash
    git commit -m "Nova mensagem de commit" --amend
    ```

#

- #### Voltando a outros commits.

Também podemos voltar a outros commits já realizados usando o comando `git reset`. Existem três tipos diferentes de reset: "soft", "mixed" e "hard". Aqui está um exemplo de como usá-los:

- **Soft Reset**: Use o soft reset para desfazer um commit, mas mantendo as alterações no estado de preparação (staging area). Por exemplo:

    ```bash
    git reset --soft commit-hash
    ```

- **Mixed Reset**: Use o mixed reset para desfazer um commit e remover as alterações da staging area, mas mantê-las nos arquivos locais. Por exemplo:

    ```bash
    git reset --mixed commit-hash
    ```

- **Hard Reset**: Use o hard reset para desfazer um commit e também descartar todas as alterações nos arquivos locais. Isso reverterá completamente para o estado do commit especificado. Por exemplo:

    ```bash
    git reset --hard commit-hash
    ```

Substitua "commit-hash" pelo hash do commit ao qual deseja retornar. Tenha cuidado com o hard reset, pois ele pode causar a perda irreversível de dados.

#

- #### Renomeando arquivo.

    Quando precisamos renomear um arquivo corretamente no Git, não basta apenas acessar a pasta e renomeá-lo. Dessa forma, o Git não conseguirá entender a mudança, pois para ele parecerá que um arquivo desapareceu e outro com um nome diferente foi adicionado. Portanto, devemos seguir assim:

    ```bash
    git mv nome-antigo nome-novo
    ```

    Substitua "nome-antigo" pelo nome atual do arquivo que deseja renomear e "nome-novo" pelo novo nome que deseja dar a ele. Com esse comando, o Git mostrará no `git status` que um arquivo foi renomeado e registrará como "(renamed)".

#

- #### Removendo arquivo.

  Quando precisamos remover um arquivo corretamente no Git, não basta apenas acessar a pasta e remove-lo. Dessa forma, o Git não conseguirá entender a mudança, pois para ele parecerá que o arquivo desapareceu. Portanto, devemos seguir assim:

    ```bash
    git rm nome
    ```

  Substitua "nome" pelo nome atual do arquivo que deseja remover. Com esse comando, o Git mostrará no `git status` que um arquivo foi removido e registrará como "(removed)".

#

- #### Consultando lista de branches.

    Com o comando abaixo, podemos ver todas as branches que existem em nosso projeto:

    ```bash
    git branch
    ```

#

- #### Criando uma nova branch

    Uma "Branch" (ramificação) é como uma bifurcação a partir de uma "base". Em vez de fazer alterações diretamente nos arquivos da base, criaremos uma nova Branch com um nome que descreve a alteração que estamos fazendo, por exemplo, "alterando_algumacoisa_do_projeto". Então, realizamos as alterações nos arquivos na Branch criada.

     ```bash
    git branch nome_da_nova_branch
    ```

    Essa abordagem de usar Branches permite que trabalhemos em diferentes recursos ou correções de bugs sem afetar diretamente o código principal.

#

- #### Navegando pelas branches.
    Podemos pular de uma branch para outra e visualizar o progresso do projeto em cada uma delas. Para fazer isso, utilizaremos o comando abaixo:

    ```bash
    git switch nome_da_branch
    ```

    Substituo "nome_da_branch" pelo nome da branch que desejo acessar. Isso me permite trabalhar em diferentes partes do projeto e acompanhar o desenvolvimento em cada uma delas de forma organizada.

#

- #### Removendo uma branch.

    Quando terminamos de trabalhar em uma branch e já fizemos o `merge` de todo o conteúdo adicionado nela para a branch "main", podemos deletá-la para manter o projeto organizado. É importante notar que, mesmo após a deleção, a branch continuará visível no GitHub normalmente.

    ```bash
    git branch -d nome_da_branch
    ```

    Substituo "nome_da_branch" pelo nome da branch que desejo excluir. Isso ajuda a manter um ambiente de trabalho limpo e organizado, enquanto ainda mantém um registro das alterações no GitHub.


    