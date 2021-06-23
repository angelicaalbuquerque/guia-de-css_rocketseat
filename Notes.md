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

É um cálculo matemático, onde, cada tipo de seletor e origem do estilo possem valores a serem considerados.

### Regra important

### At rules

### Shorthand

### Funções

### DevTools

### Cuidados com a escrita

### Vendor prefixes
