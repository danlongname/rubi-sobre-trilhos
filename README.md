# Estação de Origem

A ideia desse repositório é te guiar pelo mesmo caminho que eu segui e compartilhar minhas experiências. Mas acima de tudo, te dar um norte, não te guiar por todo o caminho de estagiário até especialista.

Você tem acesso ao índice no botão bem ao lado do README.md, fiquei sabendo disso agora.

![Índice](https://user-images.githubusercontent.com/120118163/228704536-6bd260be-8e0d-4e4b-9a60-a7db119cfb8c.png)

## Preparando o Ambiente

Vamos começar por preparar o ambiente, conhecer sites com desafios para que você aprenda na prática e também manter as boas práticas usando algumas ferramentas pra isso e guias, porque ler e aprender por conta própria é importante para você crescer nessa área.

Lembre-se que pedir ajuda quando se está completamente perdido e quando se trata de algo específico do funcionamento da sua empresa é totalmente normal e esperado. Você resolve o problema, você aprende, você ganha, sua empresa ganha, todo mundo ganha.

Esses ícones vão ser seus amigos:
![Windows](https://user-images.githubusercontent.com/120118163/227725792-d249cf5f-0410-4d51-b5b1-6b62f776c6f4.png)
![WSL](https://user-images.githubusercontent.com/120118163/227725997-459c4117-1757-4614-9241-0c592b78142d.png)
![Ubuntu](https://user-images.githubusercontent.com/120118163/227726006-510a22a5-7fe6-4c2f-a6bb-08aaf5abc5ad.png)
![macOS](https://user-images.githubusercontent.com/120118163/227725974-79c96495-bb1e-47c1-9ed6-037c425ca585.png)

Pois vão servir de alerta para quais OS o próximo passo deve ser feito.

Então, preparado? Comece sua jornada!

### Ativando o WSL no Windows

![Windows](https://user-images.githubusercontent.com/120118163/227725792-d249cf5f-0410-4d51-b5b1-6b62f776c6f4.png)

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

### Instalando Ruby

Aqui estarei seguindo o tutorial do [GoRails](https://gorails.com/) que parece resolver já alguns problemas que tive tentando instalar ambos por um método que aprendi faz tempo.

![macOS](https://user-images.githubusercontent.com/120118163/227725974-79c96495-bb1e-47c1-9ed6-037c425ca585.png)

Instale o Homebrew.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

![WSL](https://user-images.githubusercontent.com/120118163/227725997-459c4117-1757-4614-9241-0c592b78142d.png)
![Ubuntu](https://user-images.githubusercontent.com/120118163/227726006-510a22a5-7fe6-4c2f-a6bb-08aaf5abc5ad.png)
![macOS](https://user-images.githubusercontent.com/120118163/227725974-79c96495-bb1e-47c1-9ed6-037c425ca585.png)

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

### Instalando o Rails

![WSL](https://user-images.githubusercontent.com/120118163/227725997-459c4117-1757-4614-9241-0c592b78142d.png)
![Ubuntu](https://user-images.githubusercontent.com/120118163/227726006-510a22a5-7fe6-4c2f-a6bb-08aaf5abc5ad.png)
![macOS](https://user-images.githubusercontent.com/120118163/227725974-79c96495-bb1e-47c1-9ed6-037c425ca585.png)

```bash
gem install rails -v 7.0.4.3
```

![macOS](https://user-images.githubusercontent.com/120118163/227725974-79c96495-bb1e-47c1-9ed6-037c425ca585.png)

```bash
sudo installer -pkg /Library/Developer/CommandLineTools/Packages/macOS_SDK_headers_for_macOS_10.14.pkg -target /
```

### Criando e Rodando sua aplicação Ruby on Rails

![WSL](https://user-images.githubusercontent.com/120118163/227725997-459c4117-1757-4614-9241-0c592b78142d.png)
![Ubuntu](https://user-images.githubusercontent.com/120118163/227726006-510a22a5-7fe6-4c2f-a6bb-08aaf5abc5ad.png)
![macOS](https://user-images.githubusercontent.com/120118163/227725974-79c96495-bb1e-47c1-9ed6-037c425ca585.png)

```bash
rails new myapp
cd myapp
rake db:create
rails server
```

Acesse [http://localhost:3000](http://localhost:3000) e veja seu server rodando :)

### Instalando Visual Studio Code

Acesse a [página de downloads do VS Code](https://code.visualstudio.com/download) e selecione a versão específica do seu Sistema Operacional.

Talvez seja óbvio mas eu vou deixar claro que, se estiver usando o Windows com WSL, você vai instalar o VSCode no Windows, não no Ubuntu.

![Windows](https://user-images.githubusercontent.com/120118163/227725792-d249cf5f-0410-4d51-b5b1-6b62f776c6f4.png)

Depois de instalar e abrir o VS Code, [instale a extensão para desenvolvimento remoto](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack).

![WSL](https://user-images.githubusercontent.com/120118163/227725997-459c4117-1757-4614-9241-0c592b78142d.png)
![Ubuntu](https://user-images.githubusercontent.com/120118163/227726006-510a22a5-7fe6-4c2f-a6bb-08aaf5abc5ad.png)
![macOS](https://user-images.githubusercontent.com/120118163/227725974-79c96495-bb1e-47c1-9ed6-037c425ca585.png)

Para abrir um projeto dentro do VS Code, digite no terminal:

```bash
code .
```

### Configurando o Git

![WSL](https://user-images.githubusercontent.com/120118163/227725997-459c4117-1757-4614-9241-0c592b78142d.png)
![Ubuntu](https://user-images.githubusercontent.com/120118163/227726006-510a22a5-7fe6-4c2f-a6bb-08aaf5abc5ad.png)
![macOS](https://user-images.githubusercontent.com/120118163/227725974-79c96495-bb1e-47c1-9ed6-037c425ca585.png)

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

## Guias

Ler e aprender por conta própria é extremamente importante! Lá vêm material de leitura! Que com certeza te tornará um profissional melhor e mais preparado pro mercado de trabalho!

### [Ruby on Rails Guides](https://guides.rubyonrails.org/index.html)

Nada melhor do que o guia oficial da framework, não é mesmo? E com a simples proposta de: "Esses guias foram criados para torná-lo imediatamente produtivo com Rails e para ajudá-lo a entender como todas as peças se encaixam." você está em boas mãos, com certeza! Por isso, ignoramos a ordem alfabética aqui e colocamos o guia oficial acima dos guias de boas práticas.

### [Best Practices](https://rubystyle.guide/)

Este guia de estilo Ruby recomenda as melhores práticas para que os programadores Ruby do mundo real possam escrever código que possa ser mantido por outros programadores Ruby do mundo real. Um guia de estilo que reflete o uso real é usado, enquanto um guia de estilo que se apega a um ideal que foi rejeitado pelas pessoas a quem se destina corre o risco de não ser usado de forma alguma - não importa quão bom ele seja.

### [Better Specs](https://www.betterspecs.org/)

Better Specs é uma coleção de melhores práticas que os desenvolvedores aprenderam enquanto testavam aplicativos que você pode usar para melhorar suas habilidades de codificação ou simplesmente para inspiração. Better Specs nasceu na Lelylan (plataforma de nuvem IoT de código aberto) e verificar sua suíte de teste pode ser inspirador.

## Cursos e Bootcamps

Para entrar na área eu fiz um treinamento de imersão web pela [Campus Code](https://www.campuscode.com.br/), participando do programa [TreinaDev](https://treinadev.com.br/). Aprender com prática foi um método muito eficaz pra mim, então está no topo das recomendações, entretanto, você precisa ficar atento para a abertura de novas turmas e competir com outros aspirantes a desenvolvedores para seguir no programa.

### [Codecademy](https://www.codecademy.com/learn/learn-rails)

Uma escola online de código renomada que oferece cursos gratuitos de programação, incluindo Ruby on Rails. Você aprenderá a construir aplicações web com Rails, gerenciar versões com Git e implantar seus projetos no Heroku. (Agora que não tem mais Heroku gratuito, como faz?)

### [freeCodeCamp](https://www.freecodecamp.org/)

Curso online gratuito de desenvolvimento web completo, que inclui módulos sobre Ruby on Rails. O curso ensina desde HTML e CSS até desenvolvimento back-end com Ruby on Rails.

### [OneBitCode](https://onebitcode.com/lp/)

O One Bit Code oferece diversos cursos gratuitos sobre Ruby e Ruby on Rails, com aulas em vídeo e exercícios práticos. É possível aprender desde os conceitos básicos até temas avançados, como desenvolvimento de APIs e aplicações em tempo real. Você pode também aprender com o minicurso de [Minicurso de Testes para Ruby on Rails com RSpec](https://onebitcode.com/course/minicurso-de-testes/), muito recomendado.

## Noções desejáveis

Tiradas do nosso querido ChatGPT, essas seriam noções que variam de básicas, intermediárias e avançadas que seriam muito bom obter para se tornar um bom desenvolvedor Ruby on Rails.

### Lista de noções básicas

* Compreensão dos princípios básicos da linguagem Ruby, como variáveis, tipos de dados, operadores e estruturas de controle de fluxo.
* Conhecimento de como criar uma aplicação Ruby on Rails usando o comando rails new.
* Familiaridade com o conceito de MVC (Model-View-Controller) e sua implementação no framework Ruby on Rails.
* Conhecimento dos principais tipos de dados do ActiveRecord, como string, integer, float e boolean, e como usá-los em modelos.
* Familiaridade com o uso de rotas para mapear URLs a ações do controlador.
* Conhecimento básico de HTML, CSS e JavaScript, e sua integração com o Ruby on Rails.
* Compreensão do uso de formulários e validação de entrada de dados.
* Conhecimento de como criar e executar migrações de banco de dados.
* Habilidade para usar o console do Rails para interagir com a aplicação e o banco de dados.
* Compreensão de como iniciar o servidor web local e visualizar a aplicação em um navegador.

### Lista de noções intermediárias

* Conhecimento sólido da sintaxe e estrutura da linguagem Ruby.
* Compreensão dos principais conceitos do framework Ruby on Rails, como rotas, controladores, modelos, migrações e visualizações.
* Conhecimento do ActiveRecord e suas principais funcionalidades, como associações, validações, callbacks e escopos.
* Habilidade para escrever testes automatizados usando ferramentas como RSpec, Capybara e FactoryGirl.
* Conhecimento de bancos de dados relacionais, como MySQL e PostgreSQL, e habilidades em escrever consultas SQL complexas.
* Experiência em trabalhar com APIs RESTful e consumir APIs externas.
* Habilidade para integrar bibliotecas e gems de terceiros em uma aplicação Ruby on Rails.
* Conhecimento de práticas recomendadas de segurança e desempenho, como evitar vulnerabilidades de segurança, otimizar consultas de banco de dados e gerenciar cache.
* Habilidade para usar o Git para controle de versionamento de código e trabalhar em equipe usando plataformas como GitHub.
* Experiência em implantar aplicativos Ruby on Rails em servidores web, como Heroku ou AWS.

### Lista de noções avançadas

* Profundo conhecimento da arquitetura e design do framework Ruby on Rails.
* Experiência em trabalhar com bibliotecas e gems de terceiros mais complexas e menos conhecidas.
* Conhecimento avançado de banco de dados relacionais, como modelagem de dados, índices, normalização e desempenho.
* Habilidade para escrever código Ruby eficiente e otimizado, incluindo uso de técnicas como memoization e caching.
* Conhecimento avançado de testes automatizados, incluindo testes de unidade, integração e aceitação, e uso de ferramentas como Cucumber e Selenium.
* Experiência em criar APIs RESTful mais complexas e seguras, incluindo autenticação e autorização de usuários.
* Conhecimento em implementar técnicas de escalabilidade, como balanceamento de carga, clustering e caching distribuído.
* Habilidade para escrever código limpo e legível, seguindo boas práticas de programação e padrões de design.
* Experiência em trabalhar em projetos grandes e complexos em equipe, usando ferramentas de colaboração, como Trello, Slack e Jira.
* Conhecimento em implantar e gerenciar aplicativos Ruby on Rails em servidores de produção, incluindo tarefas de deploy, monitoramento e troubleshooting.

## Comunidade

Você definitivamente não está sozinho e com essas comunidades abaixo estará em boa companhia!

### [Ruby Brasil](https://t.me/rubybrasil)

Grupo no Telegram onde é possível interagir com outros desenvolvedores e ficar por dentro das novidades da área.

### [Ruby on Rails Link](https://www.rubyonrails.link/)

É um grupo no Slack que reúne uma comunidade global de desenvolvedores Ruby on Rails, onde é possível se conectar com outros profissionais, compartilhar conhecimentos, buscar ajuda e encontrar oportunidades de emprego. O grupo possui diversos canais de discussão sobre diferentes tópicos relacionados a Ruby on Rails, como desenvolvimento front-end, back-end, testes, segurança, dentre outros. Para participar, é necessário fazer um cadastro no site e receber um convite para entrar no Slack.

## Estação Terminal

Aqui vai de você, procure um certificado, procure vagas de estágio, procure fazer um networking, faça um LinkedIn forte e fale se candidate para vagas! Mais uma vez, o google (e o chatGPT) são seus amigos, não deixe de procurar por **guias**, **tutoriais**, **cheat sheets** e **documentações**!

Espero sucesso para você em sua jornada! :rocket:
