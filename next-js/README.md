# Next.js

É a versão framework do React, o React é a biblioteca JavaScript mais popular para aplicação front-end do mundo e o Next.js acrescenta ao React uma estrutura, e uma série de funcionalidades.
Framework trás essa ideia de trazer uma estrutura pré-pronta para que possamos personalizar e apartir daí começar a desenvolver nossas aplicações.

## Criando um projeto com Nest.js

- Dentro da pasta do projeto, vamos rodar o comando(mais recomendado atualmente usar o npx):

```
npx create-next-app fundamentos
                     [nome-aplicação]
```

**npx:** Comando que vai se encarregar de baixar uma dependência que vamos usar apenas de forma temporária. Ele baixa essa dependência, executa o que tem que ser executado e depois exclui ela. Desse modo, não instalamos as dependências de forma global, evitando ocupar espaço na máquina. 

**create-next-app:** Dependência para criar um projeto.

- Ao finalizar a criação ele informa no terminal os próximos passos.
Primeiro, entrar na pasta da aplicação:

```
cd fundamentos
   [nome-pasta-aplicação]
```

- Segundo, rodar o comando para iniciar o projeto:

```
yarn dev ou npm run dev
```

## Configurações do projeto

Dentro do vscode, podemos notar que foram criados os seguintes diretórios no projeto:

```
.next
node_modules
pages
public
styles
```

Vamos **criar uma pasta src na raiz do projeto**.
E **mover as pastas pages e styles para dentro de src**

- Agora, vamos parar a aplicação

```
ctrl + c
```

- E rodar novamente, para que a página seja recarregada:

```
yarn dev ou npm run dev
```

- Outra coisa, que podemos nos atentar é que dentro da pasta _pages_ temos dois arquivos:

```
_app.js
index.js
```

- Eles são arquivos javascript só que dentro deles temos códigos _jsx(javascript com react)_, desse modo, podemos mudar a extensão desses arquivos para que o vscode consiga lidar melhor com eles.

## Estrutura de pastas

- No momento vamos ressaltar 3 pastas que o next.js cria no nosso projeto:

```
public
pages
styles
```

- Sabemos que qualquer aplicação web se baseia em trẽs tecnologias: HTML, CSS e JavaScript. 
Dentro da pasta _styles_ temos os arquivos de _CSS_. E podemos notar que temos dois padrões de nomenclatura, um padrão que é simplesmente o _nome-do-arquivo.css_ que é utilizado para modificar a aplicação como um todo, de forma global(ex.: _globals.css_) e o outro padrão que é _nome-do-arquivo.module.css_ que é o CSS escopado/modularizado esse CSS vai impactar componentes especificos(ex.: _Home.module.css_).

- Já na pasta _public_ vamos ter os arquivos de imagem, fonte, video, gif. Dentro desse diretório, podemos criar subpastas, ex.: imagens, fonts... e esses arquivos serão servidos de forma estática para a aplicação.

- Como viemos do React, vamos sentir falta da página _index.html_ que vem por padrão, e se precisarmos personalizar o index, existem outras formas de fazer... assunto para outro momento.

- Na pasta _pages_ será a pasta que vamos acabar trabalhando a maior parte do tempo... dentro dela, temos o arquivo _index.jsx_ e esse arquivo está sendo carregado no localhost:3000 e temos também uma subpasta chamada _api_ e dentro dela temos o arquivo chamado _hello.js_ e se abrirmos a página localhost:3000/api/hello vamos ver os dados dessa página. Ou seja, o next.js é um framework fullstack, ele vai dar a parte do front como também vai permitir a criação da API dentro dele.

## Primeiro componente & rotas

- Primeiramente vamos excluir o arquivo _index.jsx_ que se encontra dentro do diretório _src/pages_ para aprendermos a criar ele do zero e entendermos como funciona a criação de componentes dentro do next.js.

- No novo arquivo _index.jsx_ vamos criar uma função chamada _Inicio_ e ela vai retornar/_return_ a string _"Início"_:

``` JSX
function Inicio() {
  return "Início"
}
```

- Nesse momento, não vamos conseguir ver essa informação/retorno _"Início"_ na tela, pois foi gerado o seguinte problema: _The default export is not a React Component in page: "/"_, ou seja, ele tentou acessar um componente, mais esse componente precisa ser exportado. 
Portanto, vamos voltar na função, e antes dela colocar a palavra _export_, mas isso também não será suficiente, pois precisamos exportar por padrão então devemos colocar _export default_, desse modo o retorno do componente funcional irá aparecer na tela:

``` JSX
export default function Inicio() {
  return "Início"
}
```

- Antes de prosseguirmos vale resaltar, se criarmos novos arquivos dentro da pasta _pages_, por exemplo um arquivo chamado _teste.jsx_ que vai receber um componente funcional igual ao que criarmos para _index.jsx_ cujo o retorno vai ser a string _"Teste"_:

``` JSX
export default function Teste() { // é importante exportar por padrão, para que ele consiga ler e executar esse função
  return "Teste"
}
```

- Só o fato de criarmos um novo arquivo dentro da pasta _pages_ faz com que tenhamos acesso a url localhost:3000/nome-arquivo, nesse caso a url _localhost:3000/teste_, e ela vai mostrar o conteúdo desse arquivo _teste.jsx_.
Então, a primeira coisa que devemos lembrar e entender... que o Next.js é um framework  que foca bastante em não precisarmos configurar as coisas, ou seja, vamos usar uma série de convenções e essas convenções vão nos ajudar no desenvolvimento da aplicação. E uma convenção é o fato que se criarmos um arquivo dentro da pasta _pages_, automáticamente temos acesso ao conteúdo desse arquivo em uma url seguindo o mesmo caminho de pastas desse arquivo.


## Conhecendo o JSX

É uma extensão de sintaxe para JavaScript. É recomendado usar JSX com o React. 
JSX pode lembrar uma linguagem de template, mas que vem com todo o poder do JavaScript. Nada mais é que código JavaScript com "cara" de HTML.

- Dentro do Next.js para utilizarmos o JSX não é necessário realizar o import do React no arquivo. Podemos usá-lo diretamente assim:

``` JSX
export default function Inicio() {
  return (
    <div>
      <h1>Fundamentos de Next.js & React</h1>
      <h2>Vamos estudar esse framework!</h2>
    </div>
  )
}
```

## Integração JavaScript/JSX

Como acessar o JavaScript puro dentro de um trecho JSX?
Sim, usando um par de chaves {}. Quando usamos par de chaves significa que dentro podemos usar código JavaScript. Exemplo:

```JSX
export default function Jsx() {
  const a = 2
  const b = 3
  const subtitulo = <h2>Teste</h2>
  
  return (
    <div>
      <h1>JSX é um conceito central</h1>
      {subtitulo} {/* acessando o trecho JSX da constante subtitulo */}
      <h3>{a * b}</h3> {/* vai ser feito a multiplicação e o resultado vai ser renderizado em tela */}
    </div>
  )
}
```

## CSS Global

O CSS global da nossa aplicação fica dentro da pasta _styles_ no arquivo _globals.css_ e esse arquivo está sendo referênciado dentro do arquivo _app.jsx que fica dentro da pasta pages:

``` JSX
import '../styles/globals.css' // referẽncia ao arquivo CSS global da aplicação

function MyApp({ Component, pageProps }) { // função que renderiza as páginas da aplicação
  return <Component {...pageProps} />
}

export default MyApp

```

- No arquivo _globals.css_ podemos mudar o _background-color_ para um tom de cinza e a cor da fonte/_color_ para um tom de branco, desse modo deixando a leitura mais agradável... e essas alterações vão refletir nos outros componentes também:

``` CSS globals.css
html,
body {
  font-family: -apple-system, BlinkMacSystemFont, Segoe UI, Roboto, Oxygen,
  Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif;

  padding: 0;
  margin: 0;

  background-color: #222;
  color: #eee;
}

a {
  color: inherit;
  text-decoration: none;
}

* {
  box-sizing: border-box;
}
```

- Podemos criar também outra folha de estilo para a aplicação, exemplo _app.css_ e inserir essas novas personalizações dentro desse arquivo, tirando do _globals_:

``` CSS app.css
html,
body {
  background-color: #222;
  color: #eee;
}
```

- E para que essas propriedades sejam aplicadas globalmente na nossa aplicação, vamos referênciar esse arquivo _app.css_ dentro do arquivo que renderiza as páginas da aplicação(_app.js):

``` JSX
// Local para importar css globais(podemos ter mais de um)
import '../styles/globals.css'
import '../styles/app.css'

function MyApp({ Component, pageProps }) {
  return <Component {...pageProps} />
}

export default MyApp
```

## CSS Modularizado

- Podemos excluir o arquivo _Home.module.css_, pois não iremos usar ele nessa aplicação.

- Vamos criar um novo componente no diretorio _src/pages_ chamado _estiloso.jsx_. Esse componente vai ser um componente funcional:

``` JSX
export default function Estiloso() {
  return (
    <div>
      <h1>Componente para teste de CSS Modularizado</h1>
    </div>
  )
}
```

- Agora vamos aplicar estido a esse componente. 
Podemos criar o arquivo CSS desse componente dentro da pasta _styles_ com o nome _Estiloso.module.css_ e desse arquivo podemos criar as classes CSS que acharmos necessário. Vamos criar uma classe com o nome _roxo_ que vai conter a propriedade _background-color_ com um tom de roxo e a _color_ de fonte um tom de branco:

``` CSS
.roxo {
  background-color: #542481;
  color: #fff;
}
```

- Em seguida, vamos importar essa folha de estilo dentro do componente que ela pertence(_estiloso.jsx_). Dentro de _estiloso.jsx_ vamos referênciar esse arquivo CSS(_Estiloso.module.css_) como _styles_:

``` JSX
import styles from '../styles/Estiloso.module.css'

export default function Estiloso() {
  return (
    <div>
      <h1>Componente para teste de CSS Modularizado</h1>
    </div>
  )
}
```

- Agora, podemos aplicar a classe CSS _roxo_ dentro do componente(na _div_) com a propriedade _className_ do jsx... mas para acessarmos esse estilo modularizado dentro do componente temos que referênciar dentro de um par de chaves/{} _referencia-arquivo-css.class-name_, nesse caso fica assim _styles.roxo_:

``` JSX
import styles from '../styles/Estiloso.module.css'

export default function Estiloso() {
  return (
    <div className={styles.roxo}>
      <h1>Componente para teste de CSS Modularizado</h1>
    </div>
  )
}
```

## Usando Componente

- Dentro de _src_ vamos criar uma pasta chamada _components_ e dentro dela vamos criar um componente chamado _Cabecalho.jsx_ e vamos defini-lo como um componente funcional:

``` JSX
export default function Cabecalho() {
  return (
    <header>
      <h1>Fundamentos de Next.js & React</h1>
    </header>
  )
}
```

- E vamos usar esse componente dentro de uma página. Para isso, vamos criar um arquivo chamado _exemplo.jsx_ dentro de _src/pages_. E nesse arquivo, vamos criar um componente funcional e exportar por padrão, e nele vamos importar e retornar a intância jsx do componente _Cabecalho_:

```JSX
import Cabecalho from "../components/Cabecalho";

export default function Exemplo() {
  return (
    <Cabecalho />
  )
}
```

## Propriedade de Componentes

- Agora, vamos entender como passar para um compentente uma propriedade, a fim de personalizarmos ele.
Primeiramente, em _exemplo.jsx_ vamos duplicar a referência ao componente _Cabeçalho_ a fim de reaproveitarmos esse componente, mas vale resaltar que devemos envolve-los por um elemento(se não irá ocorrer um erro), pode ser uma _div_, _table_ ou pelo proprio _React.Fragment_ que foi feito para agrupar uma lista de componentes filhos sem adicionar nós extras ao DOM:

``` JSX
import Cabecalho from "../components/Cabecalho";

export default function Exemplo() {
  return (
    <div>
      <Cabecalho />
      <Cabecalho />
    </div>
  )
}
```

- Vamos supor que queremos passar o título/h1 desse componente _Cabecalho_ de forma personalizada... então dentro dele vamos receber um parâmetro chamado _props_. E podemos notar através do _console_ que _props_ é um objeto vazio:

``` JSX
export default function Cabecalho(props) {
  console.log(props)
  return (
    <header>
      <h1>Fundamentos de Next.js e React</h1>
    </header>
  )
}
```

- E se no componente _exemplo.jsx_ dentro da referência ao componente _Cabecalho_ passarmos uma propriedade chamada _titulo_ com o texto que queremos como titulo para eles: 

``` JavaScript
import Cabecalho from "../components/Cabecalho";

export default function Exemplo() {
  return (
    <div>
      <Cabecalho titulo="Título 1"/>
      <Cabecalho titulo="Título 2"/>
    </div>
  )
}
```

- Podemos notar através do _console_ que o objeto _props_ contém essas informações de _titulo_ e podemos recupera-las atraves acessando o atributo que queremos recuperar de dentro do objeto props(_props.titulo_):

``` JSX
export default function Cabecalho(props) {
  console.log(props)
  return (
    <header>
      <h1>{props.titulo}</h1>
    </header>
  )
}
```

## Navegação entre Componentes 

- Vamos entender uma funcionalidade do Next.js para navegação entre componentes via _Link_. Vamos no arquivo _index.js_ e vamos excluir o que tem dentro da _div_ e vamos importar o _Link_ de dentro do _next/link_:

``` JSX
import Link from "next/link"

export default function Inicio() {
  return (
    <div>
      
    </div>
  )
}
```

- E com isso, vamos criar um _Link_ e dentro desse link vamos definir o atributo obrigatório _href_ que nada mais é do que o caminho para acessar o link que queremos(link do componente que foi criado pelo next) e dentro do _Link_ vamos definir o nome dele(nome do componente):

``` JSX
import Link from "next/link"

export default function Inicio() {
  return (
    <div>
      <Link href="/estiloso">
        Estilo
      </Link>
    </div>
  )
}
```

- E dentro desse componente _Estiloso_ podemos criar um _Link_ para voltar para o _index_. Vamos importar _Link_ de _next/link_ e criar o link para o _/_ com o nome _Voltar_:

``` JSX
import Link from 'next/link'
import styles from '../styles/Estiloso.module.css'

export default function Estiloso() {
  return (
    <div className={styles.roxo}>
      <Link href="/">Voltar</Link>

      <h1>Componente para teste de CSS Modularizado</h1>
    </div>
  )
}
```

## Componente Layout

- Dentro de _src/components_ vamos criar um componente que vai representar o layout da página, ele irá se chamar _Layout_. Dentro desse arquivo vamos criar um componente funcional:

``` JSX
export default function Layout(props) {
  return (
    <div>
      
    </div>
  )
}
```

- Em seguida, vamos importar o _Link_ do _next/link_ e vamos definir um link que irá voltar para o home da nossa aplicação:

``` JSX
import Link from "next/link"

export default function Layout(props) {
  return (
    <div>
      <Link href="/">Voltar</Link>

    </div>
  )
}
```

- E depois vamos passar um conteúdo para esse componente Layout... como assim? Queremos pegar o conteúdo de outro componente e renderizar na tela. Por exemplo, vamos importar o componente _Layout_ que contém o link de voltar para o home dentro do componente _Estiloso_ e vamos envolver o conteúdo desse componente _Estiloso_ com o componente _Layout_ que importamos, para ele ter sem precisarmos criar manualmente o botão/link de voltar para o home:

``` JSX
import Layout from "../components/Layout"
import styles from "../styles/Estiloso.module.css"

export default function Estiloso() {
  return (
    <Layout>
      <div className={styles.roxo}>
        <h1>Componente para teste de CSS Modularizado</h1>
      </div>
    </Layout>
  )
}
```

- Só que, se acessarmos a url do componente _Estiloso_ vamos notar que só está sendo renderizado o que está no componente _Layout_, ou seja, o link voltar. Isso ocorre, pois é necessário informar dentro do componente _Layout_ que desejamos renderizar o conteúdo que foi passado dentro dele através dos componentes filhos(props.children):

``` JSX
import Link from "next/link"

export default function Layout(props) {
  return (
    <div>
      <Link href="/">Voltar</Link>
      {props.children}
    </div>
  )
}
```

- Vamos criar uma folha de estilo para layout dentro de _src/styles_ com o nome _Layout.module.css_ e vamos referênciar esse arquivo como _styles_ dentro do seu componente:

``` JSX
import styles from "../styles/Layout.module.css"

import Link from "next/link"

export default function Layout(props) {
  return (
    <div>
      <Link href="/">Voltar</Link>
      {props.children}
    </div>
  )
}
```

- Desse modo, podemos criar uma classe e referênciar ela como _styles.nome-classe_, que nesse caso o nome da classe será layout:

``` JSX
import styles from "../styles/Layout.module.css"

import Link from "next/link"

export default function Layout(props) {
  return (
    <div className={styles.layout}>
      <Link href="/">Voltar</Link>
      {props.children}
    </div>
  )
}
```

- E podemos selecionar essa classe no arquivo _Layout.module.css_ e aplicar algumas propriedades de estilo:

``` CSS Layout.module.css
.layout {
  
}
```

- Dentro dela vamos aplicar uma altura/_height_ de _100vh_ para que o componente ocupe todo o espaço disponível, além disso, vamos definir o _display_ como _flex_ e alterar o _flex-direction_ para _column_:

``` CSS Layout.module.css
.layout {
  display: flex;
  flex-direction: column;

  height: 100vh;
}
```

- Feito isso, vamos voltar no arquivo do componente _Layout_ e vamos dividir o componente em duas partes, uma que vai conter o cabeçalho com os links e outra parte que vai conter o conteúdo, ambas as partes terão suas próprias classes CSS:

``` JSX
import styles from "../styles/Layout.module.css"

import Link from "next/link"

export default function Layout(props) {
  return (
    <div className={styles.layout}>
      <div className={styles.cabecalho}>
        <Link href="/">Voltar</Link>
      </div>
      <div className={styles.conteudo}>
        {props.children}
      </div>
    </div>
  )
}
```

- Em seguida, e essa classe _cabecalho_ que criamos para o cabeçalho vamos selecionar ela dentro da folha de estilo e iremos aplicar um _background-color_ e mudar o _display_ para _flex_ e o _justify-content_ como _flex-end_ para alinhar o texto do cabeçalho todo para a direita, e um _padding_ no eixo y(vertical) de _10px_ e no eixo x(horizontal) de _20px_:

``` CSS Layout.module.css
.layout {
  display: flex;
  flex-direction: column;

  height: 100vh;
}

.cabecalho {
  display: flex;
  justify-content: flex-end;

  padding: 10px 20px;

  background-color: #777;
}
```

- E um ponto importânte sobre o componente _Link_ que gera os links(que se encontra dentro do _Layout_) é que por trás dos panos é gerado um link/tag _a_ automáticamente, então podemos usar essa tag _a_ para aplicarmos estilo CSS nele... e vamos aplicar um _background-color_ e aplicar um _padding_ no eixo y(vertical) de _5px_ e no eixo x(horizontal) de _12px_, além disso, definir uma _border-radius_ de _5px_:

``` CSS Layout.module.css
.layout {
  display: flex;
  flex-direction: column;

  height: 100vh;
}

.cabecalho {
  display: flex;
  justify-content: flex-end;

  padding: 10px 20px;

  background-color: #777;
}

.cabecalho a {
  background-color: coral;

  padding: 5px 12px;
  border-radius: 5px;
}
```

- Em seguida, vamos usar a classe _conteudo_ que criamos para o conteúdo, iremos aplicar um _padding_ de _25px_ em todas as direções:

``` CSS Layout.module.css
.layout {
  display: flex;
  flex-direction: column;

  height: 100%;
}

.cabecalho {
  display: flex;
  justify-content: flex-end;

  padding: 10px 20px;

  background-color: #777;
}

.cabecalho a {
  background-color: coral;

  padding: 5px 12px;
  border-radius: 5px;
}

.conteudo {
  padding: 25px;
}
```