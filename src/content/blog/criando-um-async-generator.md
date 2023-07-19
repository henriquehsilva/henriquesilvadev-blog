---
title: "Criando um Async Generator"
description: "Um generator assíncrono é semelhante a um generator de sincrono em que a chamada de next() é retornada
a execução do generator até atingir a palavra-chave yield. Mas no lugar de retornar true e um objeto simples, next() retorna uma promise."
pubDate: "Jul 20 2023"
badge: "#JAVASCRIPT"
tags: ["JS", "ES6"]
---

Um <b>generator</b> assíncrono é semelhante a um <b>generator</b> sincrono em que a chamada de <b>next()</b> é retornada
a execução do generator até atingir a palavra-chave <b>yield</b>. Mas no lugar de retornar true e um objeto simples, next() retorna uma <b>promise</b>.

Você pode pensar em um <b>generator</b> assíncrono como uma combinação de uma <b>async function</b>
e uma <b>generator function</b>. Vamos escrever um exemplo que recupera URLs, usando uma <b>generator function</b>. 
Observe a palavra-chave <b>async</b> e o símbolo de asterisco <b>(*)</b> na linha 7 indicando um <b>async generator</b>:

```javascript
const srcArr = [
    'https://henriquesilva.dev/async_js/examples/1.json',
    'https://henriquesilva.dev/async_js/examples/2.json',
    'https://henriquesilva.dev/async_js/examples/3.json',
    ];

srcArr[Symbol.asyncIterator] = async function*() { // ⇒ linha 7
    let i = 0;
    for (const url of this) {
        const response = await fetch(url);
        if (!response.ok) {
            throw new Error('Unable to retrieve URL: ' + response.status);
        }
        yield response.json();
    }
};


const iterator = srcArr[Symbol.asyncIterator]();

iterator.next().then(result => {
    console.log(result.value.firstName); // ⇒ John
});

iterator.next().then(result => {
    console.log(result.value.firstName); // ⇒ Peter
});

iterator.next().then(result => {
    console.log(result.value.firstName); // ⇒ Anna
});

```