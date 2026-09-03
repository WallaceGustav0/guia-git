# 📚 Guia Prático de Git e GitHub

Este repositório foi criado com o objetivo de explicar, de forma simples e prática, os principais conceitos e comandos utilizados no **Git** e no **GitHub**.

A ideia é servir como material de consulta para estudantes e desenvolvedores que estão começando a trabalhar com controle de versão.

---

## 📌 Sumário

- [O que é Git?](#-o-que-é-git)
- [O que é GitHub?](#-o-que-é-github)
- [Git x GitHub](#-git-x-github)
- [Instalação](#-instalação)
- [Configuração inicial](#-configuração-inicial)
- [Criando um repositório](#-criando-um-repositório)
- [Clonando um repositório](#-clonando-um-repositório)
- [Entendendo o fluxo do Git](#-entendendo-o-fluxo-do-git)
- [Principais comandos](#-principais-comandos)
- [Commits](#-commits)
- [Branches](#-branches)
- [Merge](#-merge)
- [Pull](#-pull)
- [Push](#-push)
- [GitHub e colaboração](#-github-e-colaboração)
- [Desfazendo alterações](#-desfazendo-alterações)
- [Gitignore](#-gitignore)
- [Conflitos](#-conflitos)
- [Fluxo de trabalho recomendado](#-fluxo-de-trabalho-recomendado)
- [Comandos úteis](#-comandos-úteis)

---

# 🔹 O que é Git?

O **Git** é um sistema de controle de versão distribuído.

Ele permite acompanhar as alterações realizadas em arquivos de um projeto ao longo do tempo.

Com Git, podemos:

- Registrar alterações;
- Recuperar versões anteriores;
- Trabalhar em equipe;
- Criar ramificações do projeto;
- Comparar alterações;
- Unir alterações de diferentes pessoas;
- Manter um histórico do desenvolvimento.

Um projeto pode ser desenvolvido normalmente no computador e utilizar Git para controlar todas as modificações realizadas.

---

# 🔹 O que é GitHub?

O **GitHub** é uma plataforma que permite hospedar repositórios Git na internet.

Além de armazenar o código, o GitHub oferece recursos como:

- Colaboração;
- Pull Requests;
- Issues;
- Revisão de código;
- Gerenciamento de projetos;
- Documentação;
- Controle de permissões.

Git e GitHub não são a mesma coisa.

---

# 🔹 Git x GitHub

| Git | GitHub |
|---|---|
| Sistema de controle de versão | Plataforma online |
| Funciona localmente | Funciona na internet |
| Registra alterações | Hospeda repositórios |
| Pode funcionar sem internet | Normalmente depende de conexão |
| Criado para controle de versões | Oferece ferramentas de colaboração |

Uma forma simples de entender:

> **Git controla as versões do projeto. GitHub hospeda e facilita a colaboração sobre essas versões.**

---

# 🔹 Instalação

O Git pode ser baixado no site oficial:

https://git-scm.com/

Depois da instalação, podemos verificar se ele está funcionando:

```bash
git --version
```

Se o Git estiver instalado corretamente, será exibida a versão instalada.

---

# 🔹 Configuração inicial

Antes de começar a utilizar o Git, é recomendado configurar o nome e o e-mail que serão associados aos commits.

```bash
git config --global user.name "Seu Nome"
```

```bash
git config --global user.email "seu@email.com"
```

Para verificar:

```bash
git config --global user.name
```

```bash
git config --global user.email
```

## ⚠️ Atenção

A conta conectada ao VS Code e a identidade configurada no Git são conceitos diferentes.

Por exemplo, o VS Code pode estar conectado a uma conta do GitHub enquanto o Git está configurado com outro e-mail:

```text
VS Code
    ↓
Conta GitHub A

Git
    ↓
user.email = conta B
```

Por isso, quando os commits aparecem associados à pessoa errada, é importante verificar:

```bash
git config --global user.email
```

---

# 🔹 Criando um repositório

Existem duas formas bastante comuns de começar um projeto.

## Opção 1 — Criar o repositório localmente

Entre na pasta do projeto:

```bash
cd meu-projeto
```

Depois:

```bash
git init
```

O Git criará uma pasta oculta chamada:

```text
.git
```

Essa pasta contém as informações necessárias para o Git controlar o projeto.

---

# 🔹 Verificando o estado do projeto

Um dos comandos mais importantes é:

```bash
git status
```

Ele mostra informações como:

- Arquivos modificados;
- Arquivos novos;
- Arquivos preparados para commit;
- Branch atual.

Exemplo:

```text
modified: index.html
modified: style.css
```

---

# 🔹 Entendendo o fluxo do Git

O fluxo básico pode ser representado assim:

```text
ARQUIVO
   ↓
git add
   ↓
STAGING AREA
   ↓
git commit
   ↓
REPOSITÓRIO LOCAL
   ↓
git push
   ↓
GITHUB
```

Cada etapa possui uma função diferente.

---

# 🔹 git add

O comando `git add` adiciona alterações à **Staging Area**.

Para adicionar um arquivo:

```bash
git add arquivo.txt
```

Para adicionar todos os arquivos modificados:

```bash
git add .
```

Depois podemos verificar:

```bash
git status
```

---

# 🔹 git commit

O commit registra uma versão das alterações no histórico do Git.

Exemplo:

```bash
git commit -m "Adiciona tela de login"
```

Uma boa mensagem de commit deve explicar de forma objetiva o que foi alterado.

### Bons exemplos

```text
Adiciona tela de login
Corrige validação de formulário
Atualiza documentação
Adiciona cadastro de usuários
Corrige erro no cálculo do preço
```

### Evite

```text
coisas
teste
aaa
mudanças
final
```

---

# 🔹 git log

Para visualizar o histórico:

```bash
git log
```

Uma versão mais compacta:

```bash
git log --oneline
```

Exemplo:

```text
a81f23c Corrige validação de formulário
72bc912 Adiciona tela de login
14ad821 Cria estrutura inicial
```

---

# 🔹 Criando um repositório no GitHub

Depois de criar um repositório no GitHub, podemos conectar o projeto local ao repositório remoto.

Exemplo:

```bash
git remote add origin URL_DO_REPOSITORIO
```

Podemos verificar:

```bash
git remote -v
```

---

# 🔹 git push

O `push` envia os commits locais para o repositório remoto.

Exemplo:

```bash
git push origin main
```

Em muitos projetos, o branch principal é chamado de:

```text
main
```

---

# 🔹 git pull

O `pull` busca alterações do repositório remoto e tenta incorporá-las ao projeto local.

```bash
git pull
```

Um fluxo comum em equipe é:

```bash
git pull
```

Fazer as alterações:

```bash
git add .
```

Criar o commit:

```bash
git commit -m "Descrição da alteração"
```

Enviar:

```bash
git push
```

---

# 🌿 Branches

Branches permitem trabalhar em diferentes linhas de desenvolvimento.

Por exemplo:

```text
main
 │
 ├── feature/login
 │
 ├── feature/cadastro
 │
 └── bugfix/validacao
```

A branch `main` normalmente representa a linha principal do projeto.

---

# 🔹 Criando uma branch

```bash
git branch nome-da-branch
```

Para criar e entrar nela imediatamente:

```bash
git switch -c nome-da-branch
```

Exemplo:

```bash
git switch -c feature/login
```

---

# 🔹 Visualizando branches

```bash
git branch
```

A branch atual normalmente aparece marcada com `*`.

---

# 🔹 Trocando de branch

```bash
git switch main
```

Ou:

```bash
git switch feature/login
```

---

# 🔀 Merge

O `merge` é utilizado para unir alterações de uma branch em outra.

Por exemplo:

```text
main
 │
 └── feature/login
```

Depois que a funcionalidade estiver pronta:

```bash
git switch main
```

E:

```bash
git merge feature/login
```

As alterações da branch `feature/login` serão incorporadas à `main`.

---

# 🔄 Fluxo com branches

Um fluxo simples:

```bash
git switch main
```

Atualizar:

```bash
git pull
```

Criar uma branch:

```bash
git switch -c feature/nova-funcionalidade
```

Desenvolver a funcionalidade.

Depois:

```bash
git add .
```

```bash
git commit -m "Adiciona nova funcionalidade"
```

Enviar a branch:

```bash
git push -u origin feature/nova-funcionalidade
```

Depois, no GitHub, pode ser criada uma **Pull Request** para analisar e incorporar as alterações.

---

# 🔎 Pull Request

Uma Pull Request, ou **PR**, é uma solicitação para incorporar alterações de uma branch em outra.

Exemplo:

```text
feature/login
      ↓
Pull Request
      ↓
main
```

Uma PR pode ser utilizada para:

- Revisar código;
- Discutir alterações;
- Solicitar correções;
- Verificar testes;
- Aprovar o código antes do merge.

---

# ↩️ Desfazendo alterações

## Desfazer alterações de um arquivo

```bash
git restore arquivo.txt
```

Isso descarta alterações não commitadas daquele arquivo.

⚠️ Cuidado: alterações descartadas dessa forma podem ser perdidas.

---

## Retirar arquivo da Staging Area

Se você executou:

```bash
git add arquivo.txt
```

mas não queria adicioná-lo:

```bash
git restore --staged arquivo.txt
```

---

# 🧹 .gitignore

O `.gitignore` informa ao Git quais arquivos ou pastas não devem ser versionados.

Exemplo:

```gitignore
node_modules/
.env
.vscode/
__pycache__/
*.log
```

Isso é importante principalmente para evitar enviar:

- Senhas;
- Chaves de API;
- Arquivos temporários;
- Dependências;
- Arquivos gerados automaticamente.

### ⚠️ Nunca coloque senhas ou chaves secretas diretamente no repositório.

---

# ⚔️ Conflitos

Um conflito pode acontecer quando duas alterações diferentes modificam a mesma parte de um arquivo.

Exemplo:

```text
Pessoa A
    ↓
modifica linha 10

Pessoa B
    ↓
também modifica linha 10
```

O Git pode não saber automaticamente qual versão deve permanecer.

Nesse caso, o arquivo pode apresentar algo semelhante a:

```text
<<<<<<< HEAD
versão atual
=======
outra versão
>>>>>>> outra-branch
```

É necessário analisar o código, escolher a versão correta e remover os marcadores.

Depois:

```bash
git add .
```

E finalizar o processo com um commit, quando necessário.

---

# ☁️ GitHub e colaboração

Em um projeto com várias pessoas, um fluxo comum é:

```text
              GitHub
                 │
       ┌─────────┼─────────┐
       ↓         ↓         ↓
    Pessoa A  Pessoa B  Pessoa C
       │         │         │
       ↓         ↓         ↓
    Branch A  Branch B  Branch C
       │         │         │
       └─────────┼─────────┘
                 ↓
            Pull Request
                 ↓
               main
```

Cada desenvolvedor pode trabalhar em uma branch própria.

Isso reduz o risco de várias pessoas modificarem diretamente a branch principal ao mesmo tempo.

---

# 🔐 Autenticação

Para enviar código para o GitHub, o computador precisa estar autenticado.

A autenticação pode envolver:

- GitHub CLI;
- Gerenciador de credenciais;
- SSH;
- Token de acesso;
- Integração do VS Code.

É importante diferenciar:

```text
Identidade do commit
        ≠
Conta autenticada para push
```

O commit utiliza principalmente:

```bash
git config user.name
git config user.email
```

Enquanto a autenticação determina qual conta possui permissão para acessar o repositório remoto.

---

# 📋 Fluxo de trabalho recomendado

Para um projeto simples:

```bash
git pull
```

Fazer as alterações no código.

Verificar:

```bash
git status
```

Adicionar:

```bash
git add .
```

Criar commit:

```bash
git commit -m "Descrição da alteração"
```

Enviar:

```bash
git push
```

---

# 🧰 Principais comandos

| Comando | Função |
|---|---|
| `git init` | Inicializa um repositório |
| `git clone` | Clona um repositório |
| `git status` | Mostra o estado atual |
| `git add` | Adiciona alterações à staging |
| `git commit` | Registra alterações |
| `git log` | Mostra o histórico |
| `git branch` | Gerencia branches |
| `git switch` | Troca de branch |
| `git merge` | Une branches |
| `git pull` | Baixa e integra alterações |
| `git push` | Envia alterações |
| `git remote` | Gerencia repositórios remotos |
| `git restore` | Restaura arquivos |
| `git diff` | Mostra diferenças |
| `git fetch` | Busca alterações sem integrá-las |

---

# 🔍 git diff

Para visualizar alterações antes de criar um commit:

```bash
git diff
```

Isso permite verificar exatamente o que foi modificado.

Um bom hábito é sempre revisar as alterações antes de executar:

```bash
git commit
```

---

# 📥 Clonando um repositório

Para baixar um projeto existente:

```bash
git clone URL_DO_REPOSITORIO
```

Depois:

```bash
cd nome-do-projeto
```

E verificar:

```bash
git status
```

---

# 🧠 Resumo mental

Uma forma simples de memorizar o Git é:

```text
ALTEREI O CÓDIGO
       ↓
   git status
       ↓
    git add
       ↓
   git commit
       ↓
    git push
       ↓
     GitHub
```

Quando outra pessoa fizer alterações:

```text
GitHub
   ↓
git pull
   ↓
Meu computador
```

---

# 🚀 Exemplo completo

Suponha que queremos criar um projeto chamado `meu-projeto`.

```bash
mkdir meu-projeto
```

Entrar na pasta:

```bash
cd meu-projeto
```

Inicializar o Git:

```bash
git init
```

Configurar identidade:

```bash
git config user.name "Seu Nome"
git config user.email "seu@email.com"
```

Criar os arquivos do projeto.

Verificar:

```bash
git status
```

Adicionar:

```bash
git add .
```

Criar o primeiro commit:

```bash
git commit -m "Cria estrutura inicial"
```

Conectar ao GitHub:

```bash
git remote add origin URL_DO_REPOSITORIO
```

Definir a branch principal:

```bash
git branch -M main
```

Enviar para o GitHub:

```bash
git push -u origin main
```

A partir daí, o fluxo básico passa a ser:

```bash
git pull
git add .
git commit -m "Descrição da alteração"
git push
```

---

# 📖 Conclusão

Git é uma ferramenta fundamental para o desenvolvimento de software porque permite controlar a evolução de um projeto e manter um histórico das alterações.

O GitHub complementa o Git ao fornecer um ambiente online para armazenamento, colaboração, revisão e gerenciamento dos projetos.

Aprender Git não significa decorar todos os comandos. O mais importante inicialmente é compreender o fluxo:

```text
Alteração
   ↓
git add
   ↓
git commit
   ↓
git push
   ↓
GitHub
```

E, quando trabalhando em equipe:

```text
git pull
   ↓
criar branch
   ↓
desenvolver
   ↓
commit
   ↓
push
   ↓
Pull Request
   ↓
revisão
   ↓
merge
```

---

## ⭐ Comandos para começar

Se você está começando agora, concentre-se primeiro nestes comandos:

```bash
git init
git clone
git status
git add
git commit
git pull
git push
git branch
git switch
git merge
```

Depois, conforme o projeto evoluir, outros comandos e conceitos poderão ser aprendidos.