
## About
Preparing the git environment.

## Steps

### Install Git and Tools
```
$ sudo apt install git
$ sudo apt install git-cola
```

### Merge tool
```
$ sudo apt install meld
$ git config --global merge.tool meld
```

### Create SSH key
```
$ ssh-keygen -t ed25519 -C "your_email@example.com"
```

### Add SSH key to ssh-agent
```
$ eval "$(ssh-agent -s)"  # start the agent
# chmod 400 ~/.ssh/id_ed25519
$ ssh-add ~/.ssh/id_ed25519
```

### Check ssh-agent keys
```
$ ssh-add -l
```

### Create config file to GitHub
```
$ touch ~/.ssh/config
  
$ cat << EOF | tee -a ~/.ssh/config
  Host github.com
    Hostname ssh.github.com
    Port 443
    IdentityFile ~/.ssh/id_ed25519
  EOF   
```

### Add SSH public key in GitHub
- Copiar o conteúdo do arquivo ~/.ssh/id_ed25519.pub
- No GitHub, selecionar Settings > SSH and GPG keys
- Clicar no botão 'New SSH key'
- No campo 'Title' informar um nome qualquer
- No campo 'Key type' selecionar o tipo da chave
- No campo 'Key' colar o conteúdo da chave pública
- Clicar no botão 'Add SSJ key'

### Check GitHub connection
```
$ ssh -T git@github.com
```

## Using Git

### Basic
Initializing GIT repository
```
$ git init
```  

Setting user
```
$ git config user.name "..."
$ git config user.email "..."
```
  
Verificando as configurações do repositório
```
$ git config --list
```

Change history
```
$ git log
$ git log --oneline
```

Prepare files for commit
```
$ git add .
```

Commiting files
```
$ git commit -m "Primeiro commit"
```

Change branch name
```
$ git branch -M main
```

Linking the local repository to the remote server
```
$ git remote add origin https://github.com/<username>/<project-name>.git
```

Checking if the local repository has been linked to the remote server.
```
$ git remote -v
```

Sending commits to remote server
```
$ git push -u origin main
```

### Branches

Criando uma branch local
```
  $ git branch <nome-branch>
  $ git checkout <nome-branch>
```

Enviando a branch para o servidor remoto
```
$ git push -u origin <nome-branch>
```

Removendo a branch localmente
```
$ git branch -d <nome-branch>
```

Removendo a branch do servidor remoto
```
$ git push --delete origin <nome-branch>
```

### Merge

Cancelar um merge que tenha dado conflito
```
$ git merge --abort

  ou
  
$ git reset --hard
```

### Rebase

Fazendo rebase que não gere conflito
```
$ git rebase <nome-branch>
  
Obs: Quando não há conflitos, o comando acima é suficiente
```

Cancelando um rebase que tenha gerado conflito
```
$ git rebase <nome-branch>
$ git rebase --abort
```

Continuando o rebase que tenha gerado conflito
```
$ git rebase <nome-branch>

$ <aqui resolve-se os conflitos>

$ git add .

$ git rebase --continue
```

### Commit

Corrigindo a mensagem de commit
```
$ git commit --amend -m "<nova mensagem>"
  
Obs: O comando acima gera um novo commit. Verificar se tem alguem usando o commit que contem a mensagem errada.
```

Adicionando um novo arquivo num commit já feito preservando a mensagem
```
$ git commit --amend --no-edit
```

Acessando um determinado commit
```
$ git checkout <numero-commit>
```

Voltando para o último commit
```
$ git checkout master
```

### Undo changes

Como desfazer alterações de arquivos untracked?
```
$ git clean -f
```

Como desfazer alterações de arquivos tracked, ou seja, arquivos já commitados que foram alterados?
```
$ git restore <nome-arquivo> | git restore .
```
