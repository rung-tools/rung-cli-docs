.. _resources:

=========
Resources
=========

Quando um alerta de uma integração possui uma ou várias imagens, pode-se utilizar 
a propriedade *resources*. Esta propriedade permite que as imagens sejam visualizadas em 
um único comentário e em forma de carrossel, deixando os comentários mais limpos e 
objetivos.

.. image:: ../resources/resources.png

O conteúdo passado para a propriedade resources deve ser uma lista contendo as urls das
imagens geradas pelo alerta. Exemplo:

.. code-block:: javascript
   :emphasize-lines: 6,7,8,9,10

   return {
       alerts: [{
           title: 'Bananas are cheap',
           content: render(bananasPrice),
           comment: renderComment(bananasPrice),
           resources: [
              'http://www.bananas.com/banana1.jpg',
              'http://www.bananas.com/banana2.jpg',
              'http://www.bananas.com/banana3.jpg'
           ]
       }]
   };