---
title: "Criando um Async Generator"
description: "Um generator assíncrono é semelhante a um generator de sincrono em que a chamada de next() é retornada
a execução do generator até atingir a palavra-chave yield. Mas no lugar de retornar true e um objeto simples, next() retorna uma promise."
pubDate: "Jul 19 2023"
badge: "#JAVASCRIPT"
tags: ["JS", "ES6"]
---

Um <b>generator</b> assíncrono é semelhante a um <b>generator</b> sincrono em que a chamada de <b>next()</b> é retornada
a execução do generator até atingir a palavra-chave <b>yield</b>. Mas no lugar de retornar true e um objeto simples, next() retorna uma <b>promise</b>.

Você pode pensar em um <b>generator</b> assíncrono como uma combinação de uma <b>async function</b>
e uma <b>generator function</b>. Vamos escrever um exemplo que recupera dados de arquivos json passados via URLs, usando uma <b>generator function</b>. 
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

Nesse <b>generator</b>, usamos a palavra-chave <b>await</b> para aguardar a conclusão da operação de busca. 
Tal como acontece com as <b>generator functions</b> síncronas, os retornos de rendimento
o resultado para o chamador da função. Observe como este <b>async generator</b>
simplifica o processo de definição do protocolo iterável assíncrono. Não é
apenas mais fácil de escrever, mas também menos sujeito a erros.
Na produção, você também vai querer usar <b>catch()</b> para lidar com erros e mensagens rejeitadas.
Um programa bem projetado deve ser capaz de se recuperar
de erros comuns sem encerrar o aplicativo. Você pode encadear um
<b>catch()</b> da mesma forma que seu método irmão <b>then()</b>. Exemplo:

```javascript
iterator.next()
.then(result => {
    console.log(result.value.firstName);
})
.catch(error => {
    console.error('Caught: ' + error.message);
});

```
Se ocorrer um erro, <b>catch()</b> será executado com o motivo da rejeição passado como
seu argumento.