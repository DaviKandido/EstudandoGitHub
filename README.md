# Guia de Git e GitHub

## Instalação e Configuração

```sh
git config --global user.name "Seu Nome"
git config --global user.email "seuemail@example.com"
```

## Criando um Novo Repositório

```sh
mkdir meu-projeto
cd meu-projeto
git init
git status
```

## Adicionando e Commitando Arquivos

```sh
git add arquivo.txt
git add .

git commit -m "Mensagem do commit"
```

## Visualizando o Histórico

```sh
git log
```

## Criando e Trocando de Branch

```sh
git branch nova-branch  # Criar branch
git switch nova-branch  # Trocar para a branch
git switch -c nova-branch  #Alterna para uma nova branch e cria ela ao mesmo tempo
```

## Mesclando Branches

```sh
git switch main         # Ir para a branch principal
git merge nova-branch   # Mesclar a nova branch na main
```

## Conectando ao GitHub

```sh
git remote add origin https://github.com/seuusuario/seurepositorio.git
git push -u origin main
#Origin é uma convenção para o nome do **repositório** remoto
```

```sh
git push -u origin main
#-u garante que a branch principal seja rastreada com a branch remota

git push
#Nos proximos push a branch principal será rastreada com a branch remota
#Não é mais necessário -u
```

## Git pull

```sh
git pull <origin> <main> # Traz as alterações do repositório no gitHub
git fetch <origin> <main> # Trás a consciência das alterações
```

## Mostrar as ultimas alterações

```sh
git show
```

## Git Flow

```sh
git flow init
git flow feature start minha-feature
```

### Branches no Git Flow

**Principais:** `main`, `develop`

- `main`: Linha principal
- `develop`: LInha de desenvolvimento (branch dev)
- **Auxiliares:** `feature`, `release`, `hotfix`
- `feature`: Features separadas (Tudo que é novo)
- `release`: Em liberação para o usuário
- `hotfix`:

## Resolvendo Conflitos

```sh
git merge --no-ff branch-a
git mergetool  # Ferramenta para resolver conflitos
```

## Rebase

```sh
git rebase main #O rebase pega os commits de uma branch e os reaplica em outra branch. Isso cria novos commits com novos hashes, mas com o mesmo conteúdo.

# Mudar para a branch de trabalho
git checkout feature-branch

# Reaplicar os commits da 'feature-branch' sobre a 'main'
git rebase main

git rebase -i main #Rebase interativo para editar commits:

```

## Ignorando Arquivos

```sh
echo "node_modules/" >> .gitignore ## >> ADICIONA NO ARQUIVO .GITIGNORE > SOBRESCREVE O ARQUIVO
git status --ignore
cat .gitignore # MOSTRA O CONTEÚDO DO ARQUIVO .GITIGNORE
```

# Configurações git

```sh
git config --local #Defini configurações a nivel de um repositório local
git config --global #Defini configurações a nivel global
git config --system #Defini configurações a nivel do sistema
git config --list #Lista todas as configurações do git
```

## Aliases (Criação de atalhos)

```sh
git config [--local | --global | --system] alias.<comando curto> <comando longo

#Exemplos:
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.cm commit
git config --global alias.st status

#Criação de atalho "hist" para exibir o histórico formatado
git config --global alias.hist 'log --pretty=format:"%h %ad | %s%d [%an]" --graph --date=short'
```

## Desfazendo commits (Perde o historico de alterações)

```sh
git reset HEAD          # Remove arquivos do commit mas mantém no staging (não desfaz o commit)
git reset --soft HEAD~1 # Remove o último commit, mas mantém os arquivos no staging
git reset --hard HEAD~2 # Remove o penúltimo commit e descarta todas as mudanças (irrevogável)

```

## Removendo commits (Não perde o histórico de alterações)

```sh
git revert HEAD  # Reverte o último commit criando um commit de "desfazer"
git revert HEAD~2  # Reverte o penúltimo commit

git revert HEAD -m "Revertendo último commit" # Reverte o último commit com uma mensagem personalizada

git revert -m 1 <commit-hash> #reverter um merge commit
```

## Checkout (Restaurando arquivos)

O `git checkout` é um comando usado para alternar entre branches, restaurar arquivos específicos ou até mesmo criar novas branches. Ele foi parcialmente substituído pelo `git switch`, mas ainda é amplamente utilizado.

### Como funciona o Checkout?

#### 1. Alternar para outra branch:

```sh
git checkout nome-da-branch
```

Isso muda o HEAD para a branch especificada.

#### 2. Criar uma nova branch e mudar para ela:

```sh
git checkout -b nova-branch
```

Isso cria a branch `nova-branch` e já muda para ela.

#### 3. Restaurar um arquivo específico ao estado do último commit:

```sh
git checkout -- nome-do-arquivo
```

Se precisar reverter um checkout acidental, você pode usar:

```sh
git reflog
# Encontre o hash do commit antes do checkout
git reset --hard <commit-anterior>
```


