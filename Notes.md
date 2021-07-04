## Guia Estelar de CSS

### Conhecendo o CSS

CSS é um acrônimo para _Cascading Style Sheet_ (Folha de Estilo em Cascata).

É um código para criar estilos no HTML -- que, por sua vez é visto como a estrutura, enquanto o CSS é a beleza, a transformação da estrutura em algo bonito.

É importante saber que CSS não é uma linguaguem de programação, mas sim **linguaguem style sheet**, pois existe sintaxe (jeito correto de escrever as coisas).

Exemplo:

```HTML
<h1>Título Principal</h1>
```

```CSS
h1 {
  color: blue;
}
```

### Comentários

Os comentários em CSS não irão afetar seu código, muito pelo contrário: irão ajudar a lembrar blocos de códigos.

Os comentários também ajudam com dicas para leitura, facilitando que outros desenvolvedores entendam seu código.

Agora, nunca nunca esqueça de fechar um comentário. Eles começam com `/*` e terminam com `*/`.

```CSS
/* Seção Básica */
h1 {
  color: blue;
}
```

Comentários também servem para desabilitar parte do código, como:

```CSS
/*
  h1 {
    color: blue;
  }
*/
```

### Anatomia

A conexão do HTML com CSS funciona da seguinte maneira:

Entre chaves, o elemento `h1` tem a declaração CSS com sua propriedade (`color`, por exemplo), valor (`blue`, por exemplo) e `;` para fechar essa ideia.

```CSS
  h1 {
    color: blue;
    font-size: 60px;
    background: gray;
  }
```

- Selector: Nesse caso, todas as tags `h1`.
- Declaration: Tudo que está entre chaves (inclusive as chaves).
- Properties: Nesse caso, `color`, `font-size` e `background`.
- Property Value: Nesse caso, `blue`, `60px` e `gray`.

### Seletores

Os seletores HTML servem para conectar um elemento HTML com o CSS.

Alguns tipos:

- Global selector: `*`;
- Element/Type Selector: `h1, h2, p, div...`;
- ID Selector: `#box, #container`;
- Class Selector: `.red, .m-4`;
- Attribute selector;
- Pseudo-class;
- Pseudo-elements;
- Outros.

### Box model

O CSS trabalha com um conceito de caixas, que são os box models.

Toda caixa tem seus limites, com altura e largura. Toda caixa tem um conteúdo e espaços dentro dela, e espaços entre elas.

Quase tudo no são caixas no CSS. Posicionamento, tamanhos, espaçamentos, bordas, cores... Caixas podem ficar ao lado uma da outra, acima, abaixo...

Elementos HTML são caixas. É como se observasse cada um dos elementos do HTML e a comunicação com CSS fosse feita em caixas.

**Analise seus layouts como caixa para começar a entender como os elementos devem ser posicionados, como deve ser a aplicação no CSS.**

### Origem do CSS

Existem 4 formar de adicionar um estilo CSS num HTML. São elas:

#### inline

Utilizando o atributo `style`.

```HTML
<body>
  <h1 style="color: red">Título</h1>
</body>
```

#### `<style>`

Tag HTML que irá conter o CSS.

```HTML
<head>
  <style>
    h1 {
      color: red;
    }

    strong {
      color: blue;
    }
  </style>
</head>
<body>
  <h1>Título <strong>Principal</strong></h1>
</body>
```

#### `<link>`

Arquivo CSS externo. Uma das melhores práticas, pois se separara muito bem HTML e CSS.

```HTML
<head>
  <link rel="stylesheet" href="style.css">
</head>
```

_Crio o arquivo `style.css` para os estilos._

#### `@import`

Arquivo CSS externo. Por exemplo, pode ser aplicado por link no HTML ou dentro da tag `style` no head, ou, no melhor caso, sendo importado diretamente no arquivo css.

No HTML

```HTML
<style>
  @import url('https://fonts.googleapis.com/css2?family=Benne&display=swap');
</style>
```

No CSS

```CSS
@import url('https://fonts.googleapis.com/css2?family=Benne&display=swap');
```

Entretanto, essa forma não é tão indicada pois faz com que se leve um pouco mais de tempo para importar (pesquisar no Google a fonte) e colocar no site.

Geralmente, a importação de fontes via tag `<link>` é mais utilizada.

### A Cascata

Baseia-se na escolha do browser de qual regra ele aplicará; caso existam muitas regras para o mesmo elemento.

O estilo é lido de cima para baixo, sendo a base da cascata, o último estilo, o mais recente a ser aplicado.

No exemplo abaixo, o elemento `h1` ficaria com cor vermelha e não azul, mas manteria o font-size de 12px:

```css
h1 {
  color: red;
  font-size: 12px;
}

h1 {
  color: blue;
}
```

A leitura leva em consideração 3 fatores:

1. Origem do estilo;
2. Especificidade;
3. Importância.

#### Origem do estilos

inline > tag style > tag link.

A força da cascata influencia na escolha de qual "origem" será utilizada para fazer as alterações no CSS.

### Especificidade

É um cálculo matemático, onde cada tipo de seletor e origem do estilo possuem valores (forças) a serem considerados.

- 0. Universal selector, combinators e negation pseudo-class (:not())
- 1. Element type selector e pseud-elements (::before, ::after)
- 10. Classes e attribute selectors ([type="radio"])
- 100. ID selector
- 1000. Inline

Por exemplo, mesmo que eu tenha universal selector setando a cor de um element type selector `h1` para `green`, como 1 > 0, a cor do `h1` neste caso será `blue`:

```css
h1 {
  color: blue;
}

* {
  color: green;
}
```

Se eu coloco então uma classe `.title` no meu HTML e aplico no CSS, logo entende-se que 10 > 1 e então o estilo `.title` (color: red) será aplicado, mesmo que esteja acima do type selector e universal selector:

```html
<h1 class="title" id="my-title">Título</h1>
```

```css
.title {
  color: red;
}

h1 {
  color: blue;
}

* {
  color: green;
}
```

Agora, se eu aplico no CSS o `id` de `#my-title`, ele que será o de maior força sobre class > type selector > universal selector e será aplicada a cor cinza:

```css
.my-title {
  color: gray;
}

.title {
  color: red;
}

h1 {
  color: blue;
}

* {
  color: green;
}
```

Agora, por mais que eu tenha um ID aplicado no HTML/CSS, se eu insiro o estilo por `inline`, ele que terá o mais peso, conforme antes visto, e será aplicado a cor rosa:

```html
<h1 class="title" id="my-title" style="color: pink">Título</h1>
```

```css
.my-title {
  color: gray;
}

.title {
  color: red;
}

h1 {
  color: blue;
}

* {
  color: green;
}
```

Observação: pra eu conseguir sobrescrever, por exemplo, um ID de 100, eu teria que ter pelo menos 10 classes ou fazer uma junção, como `h1.title#my-title` (h1 vale 1; .title vale 10 e #my-title vale 100 = força 111).

```css
.my-title {
  color: gray;
}

.title {
  color: red;
}

h1.title#my-title {
  color: blue;
}

* {
  color: green;
}
```

Para eu buscar em profundidade, como, por exemplo, aplicar a cor cinza dentro da tag strong para a palavra "Principal", devo separar por vírgulas para que eu possa colocar mais de uma regra por conjunto de propriedades e valores.

Exemplo:

```html
<h1 class="title" id="my-title">Título <strong>Principal</strong></h1>
```

```css
/* este estilo que será aplicado ao título completo */
.my-title,
#my-title strong {
  color: gray;
}

.title {
  color: red;
}

body h1 {
  color: blue;
}

* {
  color: green;
}
```

### Regra !important

Devemos evitar o uso da regra `!important`, pois não é considerado uma boa prática por quebrar o fluxo natural da cascata.

Por exemplo, no caso abaixo, o estilo mais fraco de todos, o elemento h1, seria o aplicado, passando à frente dos mais fortes apenas por ter a regra `!important`.

Não importa, inclusive, se escrever o estilo inline. Uma vez aplicado o `!important`, ele que irá sobrescrever todas as regras possíveis de força.

```css
.my-title,
#my-title strong {
  color: gray;
}

.title {
  color: red;
}

h1 {
  color: blue !important;
}

* {
  color: green;
}
```

### At-rules

Relacionado com o comportamento do CSS, as _at-rules_ começam como sinal de `@`, seguido do identificador e valor.

Exemplos comuns:

- `@import`: Incluir um CSS externo;
- `@media`: Regras condicionais para dispositivos;
- `@font-face`: Fontes externas;
- `@keyframes`: Animações.

```CSS
@import url("http://local.com/style.css");

@media (min-width: 500px) {
  /* rules here */
}

@font-face {
  /* rules here */
}

#keyframes nameOfAnimation {
  /* rules here */
}
```

### Shorthand

É uma junção de propriedades. É uma de colocar diversas propriedades do CSS de uma maneira mais resumida e legível.

Por exemplo:

```CSS
/* background properties */
{
  background-color: #000;
  background-image: url('images/bg.gif');
  background-repeat: no-repeat;
  background-position: left top;

  /* background shorthand */
  background: #000 url('images/bg.gif') no-repeat left top;


  /* font properties */
  font-style: italic;
  font-weight: bold;
  font-size: .8em;
  line-height: 1.2;
  font-family: Arial, sans-serif;

  /* font shorthard */
  font: italic bold .8em/1.2 Arial, sans-serif;
}
```

Detalhes:

O shorthand não vai considerar propriedades anteriores, irá sobrescrever toda linha anterior (das declarações de properties separadas, nos exemplos acima).

Os valores que não forem especificados irão assumir valor padrão.

E, geralmente, a ordem descrita não importa, mas se houver muitas propriedades com valores parecidos, poderemos encontrar problemas.

**Propriedades que aceitam shorthand:**

- animation; background; border; border-bottom; border-color; border-left; border-radius; border-right; border-style; border-top; border-width; column-rule; columns; flex; flex-row; flex-flow; font; grid; grid-area; grid-column; grid-row; grid-template; list-style; margin; offset; outline; overflow; padding; place-content; place-items; place-self; text-decoration; transition... Ler mais [aqui](https://developer.mozilla.org/pt-BR/docs/Web/CSS/Shorthand_properties).

### Funções

É um tipo de valor que existe em CSS.

O nome da função é seguido de abre e fecha parenteses, onde recebe valores, que são chamados de argumentos.

Exemplos:

```css
@import url("http://urlaqui.com/style.css");

 {
  color: rgb(255, 0, 100);
  width: calc(100% - 10px);
}
```

Funções, então, são como caixas que vão receber valores, processá-los e retorná-los.

Nos casos acima, a URL "http://urlaqui.com/style.css" vai ser retornada como URL. os valores "255, 0, 100" vão ser retornados como RGB e os valores "100% - 10px" vão ser calculados e retornados.

### Cuidados com a escrita

Temos que ter cuidado com a formatação do texto, para que os estilos sejam aplicados direitinho. :)

No caso abaixo, "0auto" é um valor que não existe. Existe 0 e exite _auto_. Mas, grudados, não formam nada. E não existe espaçamento em "padding -left".

```css
p {
  /* jeito errado */
  margin: 0auto;
  padding -left: 15px;
}
```

### Vendor prefixes
