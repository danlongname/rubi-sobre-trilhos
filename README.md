# Estação de Origem

A ideia desse repositório é te guiar pelo mesmo caminho que eu segui e compartilhar minhas experiências. Mas acima de tudo, te dar um norte, não te guiar por todo o caminho de estagiário até especialista.

Vamos começar por preparar o ambiente, conhecer sites com desafios para que você aprenda na prática e também manter as boas práticas usando algumas ferramentas pra isso e guias, porque ler e aprender por conta própria é importante para você crescer nessa área.

Lembre-se que pedir ajuda quando se está completamente perdido e quando se trata de algo específico do funcionamento da sua empresa é totalmente normal e esperado. Você resolve o problema, você aprende, você ganha, sua empresa ganha, todo mundo ganha.

Então, sem mais delongas, vamos ao conteúdo!

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

![Windows](https://user-images.githubusercontent.com/120118163/227725792-d249cf5f-0410-4d51-b5b1-6b62f776c6f4.png)

Depois de instalar e abrir o VS Code, [instale a extensão para desenvolvimento remoto](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack).

Para abrir um projeto pelo VS Code no WSL, execute no terminal Ubuntu:

```bash
code .
```

## Instalando Ruby e Rails

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

## Configurando o Git

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

## Instalando o Rails

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

## Criando e Rodando sua aplicação Ruby on Rails

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

É isso, agora você já tem tudo preparado pra começar a programar! Mas ainda tenho mais sugestões para você, então, continue lendo!

---

Para entrar na área eu fiz um treinamento de imersão web pela [Campus Code](https://www.campuscode.com.br/), participando do programa [TreinaDev](https://treinadev.com.br/). Aprender com prática foi um método muito eficaz pra mim, mas como não posso sair recomendando a todo mundo ficar esperando turmas do TreinaDev abrir o tempo todo, além de que as vagas são poucas e a competição é enorme, então se eu descobrir outros processos como esse, vou marcar aqui porque eu achei super útil, enquanto isso, vou indicar outros sites que fazem papel de aprendizado interativo.

## Cursos Interativos

### [Codecademy](https://www.codecademy.com/learn/learn-rails)

Uma escola online de código renomada que oferece cursos gratuitos de programação, incluindo Ruby on Rails. Você aprenderá a construir aplicações web com Rails, gerenciar versões com Git e implantar seus projetos no Heroku. (Agora que não tem mais Heroku gratuito, como faz?)

### [Rails for Zombies](https://www.pluralsight.com/courses/code-school-rails-for-zombies)

(esse site é pago, mas você pode aproveitar o teste de 10 dias gratúitos)

Um site gamificado que ensina Rails construindo uma aplicação temática de zumbis. Você aprenderá a usar modelos, visões, controladores, rotas, migrações, associações, validações e muito mais.

### [Try Ruby](https://try.ruby-lang.org/)

Um site divertido e interativo que permite experimentar código Ruby no seu navegador. Você aprenderá o básico da sintaxe Ruby, estruturas de dados, métodos e classes.

---

Acredito que o melhor jeito de aprender boas práticas é ter uma extensão apontando todos os seus erros constantemente enquanto você coda para que não cometa os mesmos erros novamente. Inclusive eu nem sei quando instalei a extensão [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint) e ela está constantemente apontando erros nos meus README.md, e por consequencia eu estou cometendo menos erros. Então eu vou oferecer essa alternativa, junto com guias no final, que são pura leitura e nada interativos.

## Extensões do VS Code

Agora que você já tem o VS Code instalado e se você abriu dentro de um projeto Rails você vai encontrar no canto ícones, um deles é o de extensões e com ele vêm extensões recomendadas para seu projeto. Procure linters, eles vão ficar te incomodando toda vez que você digitar algo fora das boas práticas. Mas para algo mais específico tenho que recomendar:

### [Rails Full-Stack Extension Pack](https://marketplace.visualstudio.com/items?itemName=MateuszDrewniak.rails-full-stack-extension-pack)

Vem com um monte de extensões muito úteis e algumas okay, para que tudo esteja instalado e funcionando corretamente, você terá que instalar algumas gems também, então prepare-se pra rodar no terminal os comandos que irão aparecer assim que você instalar a extensão e aparecer uma mensagem de erro dizendo que tal gem não está instalada e não pode ser encontrada.

### GitHub Copilot

Vou deixar toda a descrição do chatGPT sobre ela aqui, parece importante ler:

GitHub Copilot é um assistente de programação alimentado por Inteligência Artificial, desenvolvido pela Microsoft e GitHub. Ele usa o GPT (Generative Pre-trained Transformer) - uma técnica de aprendizado profundo usada em linguagem natural - para gerar trechos de código automaticamente, com base no contexto do código existente e nos comentários do desenvolvedor.

Com o GitHub Copilot, os desenvolvedores podem escrever código mais rapidamente, economizando tempo na digitação e evitando a necessidade de procurar soluções em fóruns ou documentação. O assistente é integrado diretamente ao editor de código Visual Studio Code, permitindo que os desenvolvedores obtenham sugestões de código em tempo real à medida que digitam.

O GitHub Copilot está em fase beta e atualmente está disponível apenas para um número limitado de usuários que se inscreveram no programa beta. A ferramenta tem gerado controvérsia na comunidade de desenvolvedores, especialmente em relação a questões de propriedade intelectual e segurança de código, uma vez que pode levar ao uso indevido de trechos de código protegidos por direitos autorais ou introduzir vulnerabilidades no código gerado.

[Cadastre-se](https://github.com/features/copilot) para o trial ou por uma conta permanente] e instale a [extensão](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot) do VS Code.

![WSL](https://user-images.githubusercontent.com/120118163/227725997-459c4117-1757-4614-9241-0c592b78142d.png)

Ao instalar uma extensão do VS Code no Windows, você precisará instalar também no ambiente WSL quando abrir o VS Code por lá, mas não é assim para todas as extensões, então fique atento as quais extensões têm esses requisitos.

## Instalando gems

### Com o Gemfile

* Abra o arquivo Gemfile na raiz do seu projeto.
* Adicione a linha gem 'nome_da_gema' para a gema que deseja instalar, substituindo "nome_da_gema" pelo nome da gema que deseja instalar.
* Salve o arquivo Gemfile.
* Abra um terminal na raiz do seu projeto e execute o comando bundle install. Isso irá instalar todas as gems listadas no arquivo Gemfile.
* Se estiver instalando gems sem o Gemfile, é importante verificar as dependências manualmente e instalá-las conforme necessário.

### Sem o Gemfile

* Abra um terminal na raiz do seu projeto.
* Execute o comando gem install nome_da_gema, substituindo "nome_da_gema" pelo nome da gema que deseja instalar.
* Repita o comando gem install para cada gema adicional que deseja instalar.
* Lembre-se de que, se estiver usando o Gemfile, todas as gems devem ser instaladas com o comando bundle install para garantir que as dependências sejam resolvidas corretamente.

## Gems Recomendadas

Adianto que tem bastante coisa pra ler sobre essas gems e os links estão nos headers. Mas aprender lendo, mais uma vez, faz parte do seu trabalho. Só que você também pode procurar algum guia na internet, deve ter em algum canto.

### [Solargraph](https://github.com/castwide/solargraph)

Biblioteca Ruby que fornece recursos avançados de inteligência artificial para ajudar no desenvolvimento de aplicativos Ruby, incluindo autocompletar e documentação em tempo real.

Sinceramente, não sei como funciona, mas é requisito da extensão Solargraph, então né.

Para instalar, adicione tanto solargraph e solargraph-rails ao seu gemfile.

```Gemfile
gem 'solargraph'
gem 'solargraph-rails'
```

Configure o solargraph.yml para rodar o plugin **solagraph-rails**

```bash
solargraph config
```

Daí seu solargraph.yml será criado, nele altere o plugin:

```yaml
plugins:
  - solargraph-rails
 ```

### [RSpec-rails](https://rspec.info/documentation/6.0/rspec-rails/)

Biblioteca de teste BDD (Behavior-Driven Development) para Ruby. Ele fornece uma estrutura de teste expressiva e flexível que é fácil de ler e escrever. É uma das bibliotecas de teste mais populares para Ruby on Rails e é frequentemente usada para testar controladores, modelos e outros componentes do Rails.

Adicione ao seu Gemfile:

```Gemfile
group :development, :test do
  gem 'rspec-rails', '~> 6.0.0'
end
```

Documentação das gems que são instaladas juntas ao RSpec-rails: [rspec-core](https://rspec.info/documentation/3.12/rspec-core/), [rspec-expectations](https://rspec.info/documentation/3.12/rspec-expectations/), [rspec-mocks](https://rspec.info/documentation/3.12/rspec-mocks/).

### [Capybara](https://github.com/teamcapybara/capybara)

Biblioteca de teste para simular interações de usuário em um navegador. Ele permite testar sua aplicação como um usuário real, clicando em links, preenchendo formulários e verificando resultados. Capybara é uma ótima escolha para testes de integração em Rails.

Adicione ao seu Gemfile:

```Gemfile
gem 'capybara'
```

### [Factory Bot](https://github.com/thoughtbot/factory_bot/blob/main/GETTING_STARTED.md)

Biblioteca para criar objetos de modelo de maneira fácil e rápida em seus testes. Ele é usado para gerar dados de teste para seus modelos e simplificar o processo de criação de objetos em seus testes.

Adicione ao seu Gemfile:

```Gemfile
group :development, :test do
  gem 'factory_bot_rails'
end
```

### [SimpleCov](https://github.com/simplecov-ruby/simplecov)

Biblioteca de cobertura de teste que fornece relatórios de cobertura de código em HTML. Ele permite que você veja quais partes do seu código são testadas e quais não são. SimpleCov é uma ótima maneira de garantir que você esteja testando todo o seu código.

Adicione ao seu Gemfile:

```Gemfile
gem 'simplecov', require: false, group: :test
```

### [Faker](https://github.com/faker-ruby/faker)

Biblioteca para gerar dados falsos em seus testes. Ele é útil para criar dados de teste realistas, como nomes, endereços e números de telefone.

Adicione ao seu Gemfile:

```Gemfile
gem 'faker'
```

## Guias

Lembra que eu disse que ler era importante e aprender por conta própria também? Bom, aqui vai material de leitura! Que com certeza te tornará um profissional melhor e mais preparado pro mercado de trabalho!

### [Best Practices](https://rubystyle.guide/)

Este guia de estilo Ruby recomenda as melhores práticas para que os programadores Ruby do mundo real possam escrever código que possa ser mantido por outros programadores Ruby do mundo real. Um guia de estilo que reflete o uso real é usado, enquanto um guia de estilo que se apega a um ideal que foi rejeitado pelas pessoas a quem se destina corre o risco de não ser usado de forma alguma - não importa quão bom ele seja.

### [Better Specs](https://www.betterspecs.org/)

Better Specs é uma coleção de melhores práticas que os desenvolvedores aprenderam enquanto testavam aplicativos que você pode usar para melhorar suas habilidades de codificação ou simplesmente para inspiração. Better Specs nasceu na Lelylan (plataforma de nuvem IoT de código aberto) e verificar sua suíte de teste pode ser inspirador.

---

Em conclusão, isso é tudo que tenho pra compartilhar, se eu lembrar de mais algo ou achar algo interessante vou acrescentar aqui, e por último, deixo o que o ChatGPT 3.5 diz sobre os níveis de capacidade de desenvolvedores Ruby on Rails iniciantes, intermediários e avançados:

## Para desenvolvedores Ruby on Rails, conhecimento básico pode incluir

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

## Para desenvolvedores Ruby on Rails, conhecimento intermediário pode incluir

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

## Para desenvolvedores Ruby on Rails, conhecimento avançado pode incluir

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

---

## Estação Terminal

Aqui vai de você, procure um certificado, procure vagas de estágio, procure fazer um networking, faça um LinkedIn forte e fale se candidate para vagas! Mais uma vez, o google (e o chatGPT) são seus amigos, não deixe de procurar por **guias**, **tutoriais**, **cheat sheets** e **documentações**!

Espero sucesso para você em sua jornada! :rocket:
