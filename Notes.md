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

### Box model

### Origem do CSS

### A Cascata

### Especificidade

### Regra important

### At rules

### Shorthand

### Funções

### DevTools

### Cuidados com a escrita

### Vendor prefixes
