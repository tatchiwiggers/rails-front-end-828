# RAILS FRONT-END
Hoje nos vamos aprender a trabalhar com rails utilizando front end, ou seja como utilizar o front end da maneira certa quando no rails.

## SCSS FORWORD
É uma maneira poderosa de organizar nosso CSS, pois nos permite escrever menos CSS de forma mais simples.
- A sigla SCSS significa SASS CSS, onde a sigla SASS significa “Syntactically Awesome Style Sheets” – ou seja, Folhas de Estilo com Sintaxe Espetacular. A ideia é manter a mesma lógica do CSS (seletores, regras etc), mas de uma maneira mais organizada, intuitiva e com trechos de código facilmente reutilizáveis.
Como é isso exatamente?

***SCSS x CSS***
- SCSS permite parciais;
- SCSS possui variáveis;
- SCSS permite aninhamento;
- SCSS permite encadeamento em subclasses;
  & permite chamar o mesmo elemento dentro do aninhamento. Ex.:

# SCSS VARIABLES
`assets/stylesheets/config/_bootstrap_variables.scss`
app.scss
 $gray: red;
 $spacer: 48px;
 
 body {
   background: $gray; // Using this variable
   padding: $spacer ($spacer * 3);
 }

# SCSS NESTING

# SCSS CHAINING

# SCSS PARTIALS

# ASSET PIPELINE
Um framework para concatenar, reduzir e compactar ativos CSS e Imagens. A gem sprockets funciona dentro da pasta assets em tudo que está detro dessa pasta.

# DEFAULT
- Implementado por gem sprockets-rails 
- rails new habilita por padrão 
- trata da seguinte pasta: `app->assets`

# CSS IS LOADED IN THE LAYOUT
Como conectamos nosso CSS stylesheet dentro da nossa aplicação?
antigamente faziamos o link do css. Agora no rails fazemos dessa forma:

`<%= stylesheet_link_tag "application", media: "all", "data-turbolinks-track": "reload" %>`

`<%= javascript_pack_tag 'application', 'data-turbolinks-track': 'reload' %>`

O Turbolinks é um misto de biblioteca JavaScript e código back-end que implementa a técnica de carregamento de conteúdo no Ruby on Rails sem depender de jQuery.

# PRECOMPILATION
SCSS nos permite criar variáveis ​​e fazer o aninhamento e encadeamento - quando estamos carregando nossa página. Em segundo plano o que está acontecendo é, o gem sprockets
trabalha na compilação do scss em css. Como vocês já sabem, porque vocês ja aprenderam isso na epoca que fizeram css...
o navegador só pode ler css, ele não pode ler scss, então
ele precisa ser compilado em css para que a apliação possa funcionar.

<!-- application.scss -->
body {
  color: black;
  background-color: pink;

  &:hover {
    color: blue;
  }
}

inspecione a página e mostre os ativos no head gem sprockets está lidando essencialmente com com o diretório assets e lidando com os arquivos scss.

# CONCATENATION (1)
O asset pipeline tb é responsavel pela concatenação dos arquivos desde que criamos os partials e fazemos o import

# FINGERPRINTING
Antes, durante a semana do front-end, tínhamos que o famoso hard refresh para limpar nosso cache e conseguir visualiazar nossas modificações.
Em rails e sprockts gem, temos algo chamado finigerpriniting - e o que ele faz é adicionar um número ao final no nosso stylesheet css compilado toda vez que fazemos uma mudança em nosso arquivo scss... assim não precisamos fazer o hard refresh. Porque
uma vez que o nome do arquivo muda, o navegador carrega esse novo arquivo e ponto final. Antes de precisávamos de fazer o hard refresh para atualizar porque estávamos lidando com o mesmo arquivo, então era necessário atualizar até
o navegador reconhecer as alterações que havíamos feito.

MOSTRAR NO INSPECT - FAZER ALTERAÇÕES

O fingerprinting, ou seja a "impressão digital" é uma técnica que torna o nome de um arquivo dependente do conteúdo do arquivo. Quando o conteúdo do arquivo é alterado, o nome do arquivo também é alterado.
E toda vez que o arquivo muda, um novo arquivo é carregado.

# MINIFICATION / COMPRESSION (ZIP)
adicionar no development.rb
config.assets.css_compressor = :sass
mostrar a inspeção O QUE É MINIFICATION.

torna a aplicação mais rápida, em desenvolvimento temos que fazer isso manualmente mas na produção ele faz isso para nós automaticamente.

# DEPLOYNG TOMORROW TO HEROKU
Ao deployar a aplicação de vocês no Heroku (amanhã) ela vai ser pré-compilada para gerar os assets finais em um folder chamado public/assets.
Esse folder tem tem precedência sobre o folder assests/stylesheets, ou seja ele é mais importante ele roda antes...
Se por acaso vcs tiverem esse folder no app de vocês, vocês podem alterar o stylesheets de vocês o que for que não fará diferença. Mas vocês não precisam se preocupar com isso pq esse folder nunca é gerado em dev automaticamente, somente em produção.

Mas se vcs estiverem curiosos e quiserem ver como isso funciona basta rodar esses comandos no terminal.

# ALL ABOUT THE RAILS ASSET PIPELINE
aqui é o setup recomendado pelo le wagon
autoprefixer ajuda o css a trabalhar bem com todos os browsers
# LE WAGON CUSTOM SETUP

# STYLESHEETS ARCHITECTURE

# CSS

# Actually SCSS (Sassy CSS 💁‍♀️)

# ADDING A NEW COMPONENT

# IMAGES
Aqui estamos falando das imagens que vocês possuem, como parte do design do site de vocês e não as que o usuário vai enviar... isso veremos (amanhã).

# USING IMAGES IN VIEWS

# JAVASCRIPT
....
....
....

# WEBPACK!

webpack é um pacakage manager, ou seja, um Gerenciador de pacotes JS para projetos web. O que ele se propõe a fazer de diferente é focar em módulos da sua aplicação. Nem sempre ter todo e qualquer JavaScript/CSS do seu projeto num único arquivo é bom, por isso o webpack tem a ideia de code splitting, onde você modulariza partes reaproveitáveis do seu projeto, e isso facilita o desenvolvimento independente, por exemplo, ter uma equipe trabalhando em um módulo X e outra num módulo Y, mas ambos de um mesmo projeto.
Não é sempre que a gente faz um projeto tão grande assim, a ponto de precisar separar equipes em diferentes módulos, mas o webpack também é ideal para pequenos projetos. (modifié) 

O Turbolinks é um misto de biblioteca JavaScript e código back-end que implementa a técnica de carregamento de conteúdo no Ruby on Rails sem depender de jQuery.

# WEBPACKER
O Webpacker usa o Webpack para compilar todos os seus arquivos Javascript. Uma das grandes vantagens do Webpack é que, em dev oferece a opção de compilação do Javascript via webpack-dev-server.

# PACKS
temos que adicionar manualmente defer true para esperar que o HTML seja carregado antes de executar o script;
console.log("Hello from app/javascript/packs/application.js!");

# USAGE
APÓS A CONFIGURAÇÃO, MOSTRAR QUE AGORA PODEMOS USAR O MODAL!!

# GENERAL RULES
- Crie 1 controller separado para cada comportamento JavaScript.
- coloque o HTML ao qual você deseja aplicar esse comportamento em um stimulus data controller.
- Use data-target para selecionar elementos DOM. Não se esqueça de adicioná-los ao array targets em seu controller.
- Use data-action para acionar uma ação em um evento específico.

# EXAMPLE: UPDATE NAVBAR ON SCROLL

Objetivo: add um banner na página inicial com uma barra de navegação transparente.
Ao rolar, o fundo da barra de navegação fica branco.

Aqui Window representa uma janela contendo um documento DOM; é a propriedade document que aponta para o documento DOM carregado nessa janela.

A propriedade scrollY é uma propriedade de somente leitura da interface Window do JS e retorna o número de pixels que o documento está atualmente rolado verticalmente.E se precisarem vocês também podem obter o número de pixels em que o documento é rolado horizontalmente na propriedade scrollX.

A propriedade innerHeight é uma propriedade de somente leitura da interface Window que retorna a altura interna da janela em pixels, incluindo a altura da barra de rolagem horizontal, caso ela exista. O valor de innerHeight é obtido da altura da viewport de layout da janela.

# ADDING JAVASCRIPT PACKAGES