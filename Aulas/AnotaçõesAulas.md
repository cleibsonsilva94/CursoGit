# 📒 Anotações das Aulas 1–22 – Git
## 1. Git Status 🟢
O comando `git status` permite verificar o estado atual do repositório, mostrando quais arquivos foram modificados, adicionados ou ainda não rastreados.  
No VSCode, os arquivos são representados da seguinte forma:
| Símbolo | Significado | Descrição |
|----------|-------------|------------|
| `M` | Modified ✏️ | Arquivo modificado |
| `U` | Untracked 🆕 | Arquivo novo, ainda não adicionado ao Git |
| `A` | Added ➕ | Arquivo adicionado, pronto para commit |
| `D` | Deleted ❌ | Arquivo deletado |
| `R` | Renamed 🔀 | Arquivo renomeado |
| `C` | Copied 📄 | Arquivo copiado |
| `??` | Untracked 🆕 | Arquivo novo não rastreado |
| `!!` | Ignored 🚫 | Arquivo ignorado pelo `.gitignore` |
### 💻 Exemplo prático
```bash
$ git status  
On branch main  
Changes not staged for commit:  
  (use "git add <file>..." to update what will be committed)  
  modified:   arquivo1.txt   # Representado por M no VScd  

Untracked files:  
  (use "git add <file>..." to include in what will be committed)  
  arquivo2.txt              # Representado por U no VScd  
```
### 🔄 Diagrama simplificado do fluxo de arquivos no Git
```
[Arquivo não rastreado (U) 🆕]
          |
       git add ➡️
          v
[Arquivo preparado para commit (A) ➕]
          |
       git commit ✅
          v
[Arquivo registrado no repositório local 📦]
```
## 2. Git Remote 🌐
O comando `git remote` permite conectar seu repositório local a um repositório remoto, geralmente hospedado no **GitHub**, **GitLab** ou **Bitbucket**.
### 💻 Principais comandos do Git Remote
| Comando | Descrição | Exemplo |
|----------|------------|----------|
| `git remote -v` | Mostra os repositórios remotos configurados | `origin https://github.com/usuario/repositorio.git (fetch)` |
| `git remote add <nome> <url>` | Adiciona um novo repositório remoto | `git remote add origin https://github.com/usuario/repositorio.git` |
| `git remote remove <nome>` | Remove um repositório remoto | `git remote remove origin` |
| `git remote rename <nome_atual> <novo_nome>` | Renomeia um repositório remoto | `git remote rename origin upstream` |
### 📝 Exemplo prático
```bash
# Adicionando um repositório remoto
git remote add origin https://github.com/usuario/repositorio.git  

# Verificando os remotos
git remote -v  

# Removendo um repositório remoto
git remote remove origin
```
### 🔗 Diagrama simplificado do repositório remoto
```
[Repositório Local 📂]
        |
  git push / git pull ↕️
        v
[Repositório Remoto 🌐 (GitHub, GitLab, etc.)]
```
## 3. Git Commit 📝
Existem duas formas comuns de criar commits no Git:
| Comando | Descrição |
|----------|------------|
| `git commit -m "Mensagem"` | Cria um commit de **arquivos específicos** que já foram adicionados com `git add <arquivo>`. |
| `git commit -a -m "Mensagem"` | Adiciona **todos os arquivos modificados** e cria um único commit, sem precisar usar `git add` antes. |
**Resumo rápido:**  
- `-m` → Commit de arquivos já adicionados.  
- `-a -m` → Adiciona e commita tudo de uma vez.
## 4. Git Status (Revisão) 📋
O comando `git status` permite verificar o **estado atual do repositório**, mostrando arquivos modificados, adicionados, novos ou ignorados.
## 5. Movendo o Repositório Git para Outra Pasta 📂➡️📁
Durante a configuração do ambiente, foi necessário mover o controle do Git da pasta `Trilha` para dentro da subpasta `Git`, garantindo que o `.git` ficasse localizado corretamente no diretório desejado.
### ⚙️ Passo a passo resumido
```bash
# 1. Acessar a pasta principal
cd "C:\Users\clelima\OneDrive - Deloitte (O365D)\Documents\CDG_Test\Trilha"

# 2. Remover o repositório Git antigo (no PowerShell)
Remove-Item -Recurse -Force .git

# 3. Entrar na pasta Git
cd Git

# 4. Inicializar um novo repositório Git
git init

# 5. Conectar ao repositório remoto existente
git remote add origin https://github.com/cleibsonsilva94/CursosTrilha.git

# 6. Baixar o histórico remoto (sem mesclar ainda)
git fetch origin

# 7. Vincular a branch local à remota
git checkout -b master origin/master

# 8. Confirmar se a branch está rastreando corretamente
git branch -vv

# 9. (Opcional) Atualizar os arquivos locais
git pull
```
### 🧹 Git Reset Hard
```bash
git reset --hard origin/master
```
**O que faz:**  
Força o branch local a ficar **idêntico** ao branch remoto `master`, descartando todas as alterações locais (incluindo arquivos não commitados).  
**Quando usar:**  
Para **descartar tudo o que foi feito localmente** e sincronizar com o remoto.  
**Aviso ⚠️:**  
Perde todas as alterações locais não salvas.  
**Visualização simples:**
```
Antes:
Local:  A - B - C  (alterações locais)
Remoto: A - B

Depois:
Local:  A - B  (igual ao remoto)
Remoto: A - B
```
📘 **Resumo geral:**  
- `git status` → Mostra o estado dos arquivos.  
- `git remote` → Conecta e gerencia repositórios remotos.  
- `git commit` → Registra alterações locais.  
- `git reset --hard` → Restaura o estado original do repositório.  
- Estruture sempre seu ambiente Git corretamente antes de versionar os arquivos.


## 6. Git Merge 🔀
O comando `git merge` é usado para **combinar alterações de diferentes branches** em uma única linha de desenvolvimento.  
Ele integra o histórico de commits de uma branch (como `feature` ou `dev`) à branch atual (como `main`).

### 💻 Git Merge
| Comando | Descrição | Exemplo |
|----------|------------|----------|
| `git merge <branch>` | Mescla a branch especificada com a branch atual | `git merge feature-login` |
| `git merge --no-ff <branch>` | Cria um novo commit de merge, mesmo se puder ser feito como fast-forward | `git merge --no-ff feature-login` |
| `git merge --abort` | Cancela um merge em andamento em caso de conflitos | `git merge --abort` |
| `git log --graph --oneline` | Visualiza o histórico de merges e commits em formato gráfico | `git log --graph --oneline` |

### ⚙️ Passo a passo de uso
```bash
# 1. Verifique em qual branch você está
git status

# 2. Altere para a branch que receberá as alterações
git checkout main

# 3. Faça o merge da outra branch
git merge feature-login

# 4. Resolva conflitos (se houver)
# Edite os arquivos com conflito e depois:
git add .
git commit