# Apps assíncronas

O Rung possui dois tipos de chamada de retorno para a função principal. Um
app pode ser síncrona ou assíncrona. Um app síncrona executa linha
a linha e tem seu valor processado retornado. É o caso, por exemplo, de um
app que parabenize o indivíduo no seu aniversário. Quando um app
precisa "esperar" uma resposta, temos o caso de um app assíncrona.
Exemplos são requisições HTTP.

Para diferenciar apps síncronas e assíncronas, utilizamos um segundo
parâmetro na função principal, o ``done``. Quando o ``done`` é passado,
app não termina de executar até que a função ``done`` seja chamada com os
cartões a serem gerados. Na outra situação, o app termina sua execução até
quando o primeiro ``return`` for encontrado.


## App síncrona

``` js
function main(context) {
    return {
        cards: ["Hello world!"]
    }
}
```

## App assíncrona

```js
function main(context, done) {
    setTimeout(() => {
        done({
            cards: ["Hello world!"]
        });
    }, 3000);
}
```

No segundo exemplo, o app leva 3 segundos para executar e então gerar o
cartão ``Hello world!``.