
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

