.. _async_extensions:

=====================
Extensões assíncronas
=====================

O Rung possui dois tipos de chamada de retorno para a função principal. Uma
extensão pode ser síncrona ou assíncrona. Uma extensão síncrona executa linha
a linha e tem seu valor processado retornado. É o caso, por exemplo, de uma
extensão que parabenize o indivíduo no seu aniversário. Quando uma extensão
precisa "esperar" uma resposta, temos o caso de uma extensão assíncrona.
Exemplos são requisições HTTP.

Para diferenciar extensões síncronas e assíncronas, utilizamos um segundo
parâmetro na função principal, o ``done``. Quando o ``done`` é passado, a
extensão não termina de executar até que a função ``done`` seja chamada com os
alertas a serem gerados. Na outra situação, a extensão termina sua execução até
quando o primeiro ``return``.


**Extensão síncrona**

.. code-block:: javascript
   :emphasize-lines: 1

   function main(context) {
       return {
           alerts: ["Hello world!"]
       }
   }

**Extensão assíncrona**

.. code-block:: javascript
   :emphasize-lines: 1, 3

   function main(context, done) {
       setTimeout(() => {
           done({
               alerts: ["Hello world!"]
           });
       }, 3000);
   }

No segundo exemplo, a extensão leva 3 segundos para executar e então gerar o
alerta ``Hello world!``.