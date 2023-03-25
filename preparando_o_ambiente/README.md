# Estação de Origem
Daqui vamos preparar o ambiente para que você possa ir do zero até rodar o server localmente com o Rails.

## Ativando o WSL no Windows
_Você deve estar executando o Windows 10 versão 2004 e superior (Build 19041 e superior) ou o Windows 11 para usar os comandos abaixo._

Abra o Powershell (pode apertar o iniciar e digitar Powershell que ele aparecerá, é bom criar um atalho para ele depois) e execute:
```powershell
wsl --install
```
Reinicie o PC.

Abra a distribuição Ubuntu que será instalada por padrão pelo menu iniciar, ou então abra o Powershell e execute:
```powershell
Ubuntu
```
Você receberá um prompt pra criar um usuário e senha, crie ambos e siga em frente.

Ainda no terminal do Ubuntu, já atualize seus repositórios:
```bash
sudo apt update && sudo apt upgrade
```
Sempre que quiser abrir o WSL, use o Ubuntu pelo menu iniciar, ou crie outro atalho para ele.

Daqui pra frente, especificarei no heading se o passo é para um OS específico ou para todos.

## Instalando Virtual Studio Code
Acesse a [página de downloads do VS Code](https://code.visualstudio.com/download) e selecione a versão específica do seu Sistema Operacional.

Talvez seja óbvio mas eu vou deixar claro que, se estiver usando o Windows com WSL, você vai instalar o VSCode no Windows, não no Ubuntu.

### Windows
Depois de instalar e abrir o VS Code, [instale a extensão para desenvolvimento remoto](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack).

Para abrir um projeto pelo VS Code no WSL, execute no terminal Ubuntu:
```bash
code .
```

## Instalando Ruby e Rails
Aqui estarei seguindo o tutorial do [GoRails](https://gorails.com/) que parece resolver já alguns problemas que tive tentando instalar ambos por um método que aprendi faz tempo.
### macOS
Instale o Homebrew.
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
### Windows (WSL), Ubuntu e macOS
Instale dependências necessárias para o Ruby caso já não venham junto com a versão da sua distro.
```bash
sudo apt-get update
sudo apt-get install git-core zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev software-properties-common libffi-dev
```
Instale o ASDF, que é um gerenciador de versões.
```bash
cd
git clone https://github.com/excid3/asdf.git ~/.asdf
echo '. "$HOME/.asdf/asdf.sh"' >> ~/.bashrc
echo '. "$HOME/.asdf/completions/asdf.bash"' >> ~/.bashrc
echo 'legacy_version_file = yes' >> ~/.asdfrc
exec $SHELL
```
É necessário instalar plugins para cada linguagem usada, Node.js vai ser usada pro front-end então:
```bash
asdf plugin add ruby
asdf plugin add nodejs
```
Depois instale o Ruby e atualize para a última versão do Rubygems.
```bash
asdf install ruby 3.2.1
asdf global ruby 3.2.1
gem update --system
```
Então agora, vamos instalar o Node.js e Yarn (que será usado pro front-end também).
```bash
asdf install nodejs 18.15.0
asdf global nodejs 18.15.0
npm install -g yarn
```
## Configurando o Git
### Windows (WSL), Ubuntu e macOS
Substitua o username e email por seus próprios da sua conta do Github e já gere a chave ssh para permitir que faça push para seu repositório.
```bash
git config --global color.ui true
git config --global user.name "TEUNOMEDEUSUARIO"
git config --global user.email "TEUEMAILCADASTRADO@NOGIT.COM"
ssh-keygen -t ed25519 -C "TEUEMAILCADASTRADO@NOGIT.COM"
```
Pega a chave que acabou de gerar.
```bash
cat ~/.ssh/id_ed25519.pub
```
Depois de rodar o comando, a chave vai estar na tela, é só copiar.

Acesse essa página do [Github](https://github.com/settings/ssh).

Clique em: **New SSH Key**.

Dê um título e cole a chave que está na área de transferência.

Clique em **Add SSH Key**.
## Instalando o Rails
### Windows (WSL), Ubuntu e macOS
```bash
gem install rails -v 7.0.4.3
```
### macOS
```bash
sudo installer -pkg /Library/Developer/CommandLineTools/Packages/macOS_SDK_headers_for_macOS_10.14.pkg -target /
```
# Estação Terminal
## Criando e Rodando sua aplicação Ruby on Rails
### Windows (WSL), Ubuntu e macOS
```
rails new myapp
cd myapp
rake db:create
rails server
```
Acesse http://localhost:3000 e veja seu server rodando :)
