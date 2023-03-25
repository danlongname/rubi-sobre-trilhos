# Estação de Origem

Acredito que o melhor jeito de aprender boas práticas é ter uma extensão apontando todos os seus erros constantemente enquanto você coda para que não cometa os mesmos erros novamente. Inclusive eu nem sei quando instalei a extensão [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint) e ela está constantemente apontando erros nos meus README.md, e por consequencia eu estou cometendo menos erros. Então eu vou oferecer essa alternativa, junto com guias no final, que são pura leitura e nada interativos.

## Gems e Extensões do VS Code

Agora que você já tem o VS Code instalado e se você abriu dentro de um projeto Rails você vai encontrar no canto ícones, um deles é o de extensões e com ele vêm extensões recomendadas para seu projeto. Uma delas talvez seja a [Ruby Extension Pack](https://marketplace.visualstudio.com/items?itemName=walkme.Ruby-extension-pack), eu instalei e com ela vem o requisito de instalar a gem Solargraph, é só rodar no terminal e seguir em frente.

```bash
gem install solargraph
```

Ela acaba instalando junto a gem Rubocop e a extensão [ruby-rubocop](https://marketplace.visualstudio.com/items?itemName=misogi.ruby-rubocop) que aparentemente não está mais sendo mantida, então vamos desinstalar essa e instalar a [ruby-robocop-revived](https://marketplace.visualstudio.com/items?itemName=LoranKloeze.ruby-rubocop-revived) no lugar e ser feliz. O que vai acontecer de agora em diante é que você vai receber na tela vários sinais de erro toda vez que fugir das boas práticas, então, aprenda na base do "não quero mais ver erro na tela!".

## Guias

### [Best Practices](https://rubystyle.guide/)

Este guia de estilo Ruby recomenda as melhores práticas para que os programadores Ruby do mundo real possam escrever código que possa ser mantido por outros programadores Ruby do mundo real. Um guia de estilo que reflete o uso real é usado, enquanto um guia de estilo que se apega a um ideal que foi rejeitado pelas pessoas a quem se destina corre o risco de não ser usado de forma alguma - não importa quão bom ele seja.

### [Better Specs](https://www.betterspecs.org/)

Better Specs é uma coleção de melhores práticas que os desenvolvedores aprenderam enquanto testavam aplicativos que você pode usar para melhorar suas habilidades de codificação ou simplesmente para inspiração. Better Specs nasceu na Lelylan (plataforma de nuvem IoT de código aberto) e verificar sua suíte de teste pode ser inspirador.

### [testRigor](https://testrigor.com/ruby-on-rails-testing/)

Instruções do que se testar em sua aplicação e como devem ser feitos, tais como testes unitários, de integração e sistema.

## Estação Terminal

Acaba que eu aprendi mesmo mais pelos linters do VSCode (que aconselho procurar) do que olhando pra guias, mas, às vezes eles são úteis, então é bom tê-los ao alcance das mãos!

Não tenho mais linhas para te recomendar também, então fique livre para dar uma olhada nas linhas que ainda não viu!
