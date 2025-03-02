# Guia de Git e GitHub

## Instalação e Configuração

Instale o git no Windows: [https://git-scm.com/download/win](https://git-scm.com/download/win) 

```sh
sudo apt-get install git # Instale o git no linux
```

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
- 
**Auxiliares:** `feature`, `release`, `hotfix`
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
git config --global alias.ci commit
git config --global alias.st status

#Criação de atalho "hist" para exibir o histórico formatado
git config --global alias.hist 'log --pretty=format:"%h %ad | %s%d [%an]" --graph --date=short' 

```


