---
title: "Usando um Generator Function para definir um interador personalizado"
description: "As generator functions aprimoram o processo de definição do protocolo iterável
fornecendo um algoritmo iterativo. Quando chamada, uma generator function não
executar seu corpo imediatamente. Em vez disso, ele retorna um tipo especial de iterador
conhecido como um generator object, conforme mostrado na imagem a seguir."
pubDate: "Jul 20 2023"
badge: "#JAVASCRIPT"
tags: ["JS", "ES6"]
---

As <b>generator functions</b> aprimoram o processo de definição do protocolo iterável
fornecendo um algoritmo iterativo. Quando chamada, uma <b>generator function</b> não
se executa seu corpo imediatamente. Em vez disso, ele retorna um tipo especial de iterador
conhecido como <b>generator object</b>, conforme mostrado na imagem a seguir.

![Generator Function Cycle](/generatorFunctionCycle.jpg "Generation Function Cycle")

Podemos executar o corpo da <b>generator function</b> chamando seu método <b>next()</b>. 
O <b>yield</b> palavra-chave que pausa o <b>generator</b> e especifica o <b>valor</b> a ser retornado. 
Vamos demostrar em um algoritmo fácil de implementar.
Observe o <b>asterisco</b> após a palavra-chave function na linha 5. Este é o nosso <b>generator function</b>
e define um iterador personalizado para coleção:

```javascript
const collection = {
    a: 10,
    b: 20,
    c: 30,
    [Symbol.iterator]:  function* () { // ⇒ linha 5
        for (let key in this) {
            yield this[key];
        }
    }
}

const iterator = collection[Symbol.iterator]();

console.log(iterator.next()); // ⇒ {value: 10, done: false}
console.log(iterator.next()); // ⇒ {value: 20, done: false}
console.log(iterator.next()); // ⇒ {value: 30, done: false}
console.log(iterator.next()); // ⇒ {value: undefined, done: true}

```

Usamos um loop <b>for...in</b> dentro do generator para iterar sobre as propriedades do objeto. 
A cada iteração, a palavra-chave <b>yield</b> interrompe a execução do loop e
retorna o valor da propriedade seguinte ao <b>caller</b>.
É possível chamar uma <b>generator function</b> quantas vezes forem necessárias, e cada
vez que é chamado ele retorna um novo <b>generator object</b>. 
Mas um <b>generator object</b> pode ser iterado apenas uma vez. 
Como o objeto retornado por um <b>generator</b> é sempre um <b>iterador</b>,
pode usar a sintaxe <b>for...of</b> para iterar sobre o resultado também.

```javascript
for (let value of collection) {
    console.log(value);
}

// return
// 10
// 20
// 30

const collection2 = {
    a: 10,
    b: 20,
    c: 30
}

for (let value of collection2) {
    console.log(value);
}

// return
// TypeError: collection2 is not iterable
```

Agora que sabemos como funcionam os <b>generators</b> síncronos, vamos ver como funciona as chamadas assíncronas:

[Criando um Async Generator Function](https://henriquesilva.dev/blog/criando-um-async-generator)