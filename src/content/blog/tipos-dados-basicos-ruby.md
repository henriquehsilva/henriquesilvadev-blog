---
title: "Tipos de Dados Básicos no Ruby"
description: "O Ruby é uma linguagem de programação totalmente orientada a objetos, o que significa que absolutamente tudo nele é um objeto, incluindo os tipos de dados mais básicos."
pubDate: "Mar 22 2025"
badge: ""
tags: ["FUNDAMENTOS DE RUBY", "SINTAXE BÁSICA"]
slug: "tipos-dados-basicos-ruby"
heroImage: "https://www.youtube.com/embed/0-CsYaE6l08"
---

O Ruby é uma linguagem de programação totalmente orientada a objetos, o que significa que absolutamente tudo nele é um objeto, incluindo os tipos de dados mais básicos. Neste guia, exploraremos quatro desses tipos fundamentais: números (inteiros e floats), strings, símbolos e valores booleanos (`true`, `false` e `nil`).

Para acompanhar os exemplos apresentados, você pode utilizar o `irb` (Interactive Ruby) ou ambientes online como o [Try ruby](https://try.ruby-lang.org/playground/).

---

## Números

O Ruby suporta todas as operações matemáticas típicas que você esperaria:

```ruby
# Adição
1 + 1   #=> 2

# Subtração
2 - 1   #=> 1

# Multiplicação
2 * 2   #=> 4

# Divisão
10 / 5  #=> 2

# Exponenciação
2 ** 2  #=> 4
3 ** 4  #=> 81

# Módulo (resto da divisão)
8 % 2   #=> 0  (8 / 2 = 4; sem resto)
10 % 4  #=> 2  (10 / 4 = 2 com resto 2)
```

### Inteiros e Floats

Existem dois principais tipos numéricos no Ruby:

- **Inteiros:** Números inteiros, como `10`.
- **Floats:** Números com ponto decimal, como `10.5`, `10.0` ou `0.25`.

Operações entre dois inteiros resultam sempre em um inteiro:

```ruby
17 / 5    #=> 3, não 3.4
```

Para obter um resultado preciso, basta que um dos números seja um float:

```ruby
17 / 5.0  #=> 3.4
```

### Convertendo Tipos Numéricos

O Ruby facilita a conversão entre inteiros e floats:

```ruby
# Converter um inteiro para float:
13.to_f   #=> 13.0

# Converter um float para inteiro:
13.0.to_i #=> 13
13.9.to_i #=> 13
```

### Métodos Numéricos Úteis

- **`even?`**: Verifica se o número é par.
- **`odd?`**: Verifica se o número é ímpar.

```ruby
6.even? #=> true
7.even? #=> false

6.odd? #=> false
7.odd? #=> true
```

---

## Strings

Strings são sequências de caracteres e podem ser definidas com aspas duplas (`""`) ou simples (`''`).

### Concatenação

```ruby
# Com o operador de adição:
"Bem-vindo " + "a " + "Programação!"    #=> "Bem-vindo a Programação!"

# Com o operador shovel:
"Bem-vindo " << "a " << "Programação!"  #=> "Bem-vindo a Programação!"

# Com o método concat:
"Bem-vindo ".concat("a ").concat("Programação!")  #=> "Bem-vindo a Programação!"
```

### Substrings

```ruby
"olá"[0]      #=> "o"
"olá"[0..1]   #=> "ol"
"olá"[0, 2]   #=> "ol"
"olá"[-1]     #=> "á"
```

Para mais detalhes, consulte a [documentação do método `slice`](https://docs.ruby-lang.org/en/3.0.0/String.html#method-i-slice).

### Caracteres de Escape

Caracteres de escape permitem incluir caracteres especiais em strings:

```ruby
"Primeira linha\nSegunda linha"
```

---

## Símbolos

Símbolos são semelhantes a strings, mas são imutáveis e únicos, tornando-os mais eficientes em termos de desempenho quando o mesmo valor é usado repetidamente:

```ruby
:símbolo
```

Eles são frequentemente usados como identificadores ou chaves em hashes.

---

## Booleanos

O Ruby possui três valores booleanos principais:

- **`true`**: Representa verdadeiro.
- **`false`**: Representa falso.
- **`nil`**: Representa a ausência de valor ou "nada".

Esses valores são fundamentais para controle de fluxo e expressões condicionais no Ruby.

---

Este guia abrange os conceitos básicos dos tipos de dados no Ruby. Para aprofundar seus conhecimentos, explore a [documentação oficial do Ruby](https://www.ruby-lang.org/pt/documentation/).

