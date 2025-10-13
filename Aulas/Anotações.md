# 📒 Anotações das Aulas 1-22 – Git

## 1. Git Status 🟢

O comando `git status` permite verificar o estado atual do repositório, mostrando quais arquivos foram modificados, adicionados ou ainda não rastreados. No VSCode, os arquivos são representados da seguinte forma:  

- `M` (Modified) ✏️ → Arquivo modificado  
- `U` (Untracked) 🆕 → Arquivo novo, ainda não adicionado ao Git  
- `A` (Added) ➕ → Arquivo adicionado ao Git, pronto para commit  
- `D` (Deleted) ❌ → Arquivo deletado  
- `R` (Renamed) 🔀 → Arquivo renomeado  
- `C` (Copied) 📄 → Arquivo copiado  
- `??` (Untracked) 🆕 → Arquivo novo não rastreado  
- `!!` (Ignored) 🚫 → Arquivo ignorado pelo `.gitignore`

Exemplo:

$ git status  
On branch main  
Changes not staged for commit:  
  (use "git add <file>..." to update what will be committed)  
  modified:   arquivo1.txt   # Representado por M no VSCode  

Untracked files:  
  (use "git add <file>..." to include in what will be committed)  
  arquivo2.txt              # Representado por U no VSCode  

### 🔄 Diagrama simplificado do fluxo de arquivos no Git

[Arquivo não rastreado (U) 🆕]  
          |  
       git add ➡️  
          v  
[Arquivo staged / preparado para commit (M) ✏️]  
          |  
       git commit ✅  
          v  
[Arquivo registrado no repositório local 📦]  

## 2. Git Remote 🌐

O comando `git remote` permite conectar seu repositório local a um repositório remoto, geralmente hospedado no GitHub, GitLab ou Bitbucket.  

### 💻 Principais comandos do Git Remote

Comando | Descrição | Exemplo  
---------|-----------|---------  
git remote -v | Mostra os repositórios remotos configurados | origin https://github.com/usuario/repositorio.git (fetch)  
git remote add <nome> <url> | Adiciona um novo repositório remoto | git remote add origin https://github.com/usuario/repositorio.git  
git remote remove <nome> | Remove um repositório remoto | git remote remove origin  
git remote rename <nome_atual> <novo_nome> | Renomeia um repositório remoto | git remote rename origin upstream  

### 📝 Exemplo prático

# Adicionando um repositório remoto  
git remote add origin https://github.com/usuario/repositorio.git  

# Verificando os remotos  
git remote -v  

# Removendo um repositório remoto  
git remote remove origin  

### 🔗 Diagrama simplificado do repositório remoto

[Repositório Local 📂]  
        |  
  git push / git pull ↕️  
        v  
[Repositório Remoto 🌐 (GitHub, GitLab, etc.)]

Git commit -m x git commit -a -m "Mensagem"

O git commit -m voce pode comitar um arquivo especifico que está adicionado. 
O git commit -a -m voce adiciona todos os arquivos a um unico commit


## Commit

- `git commit -m "Mensagem"`  
  Permite criar um commit de um **arquivo específico** que já foi adicionado (`git add <arquivo>`).

- `git commit -a -m "Mensagem"`  
  Adiciona **todos os arquivos modificados** ao commit de uma única vez, sem precisar usar `git add` para cada arquivo.

---

## Status

O comando `git status` permite verificar o **estado atual do repositório**, mostrando quais arquivos foram modificados, adicionados ou ainda não rastreados.  

No VSCode, os arquivos são representados da seguinte forma:
