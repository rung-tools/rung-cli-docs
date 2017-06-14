.. _param_types:

===================
Tipos de parâmetros
===================

Os parâmetros de entrada de uma extensão do Rung possuem diversos tipos com
múltiplas finalidades, que variam de acordo com como você vai trabalhar com
o dado e como você deseja que ele seja renderizado para o usuário durante
a instalação. Os tipos podem ser importados via:

.. code-block:: javascript

   import {} from 'rung-cli/dist/types';

-------
Integer
-------

Para números inteiros tendendo de negativo a infinito positivo, a depender da
representação de números inteiros em bits de onde está rodando.

------
Double
------

Para números de ponto flutuante (decimais), a depender da representação de
números de ponto flutuante em bits de onde está rodando, geralmente segundo
a IEEE754_.

--------
DateTime
--------

*Indisponível*

-------
Natural
-------

Números naturais de 0 a infinito. Não são aceitos números negativos

-------
Char(n)
-------

Textos de até ``n`` caracteres, onde ``n`` corresponde a um número natural.
Se tiver como entrada um texto maior, este é cortado até o limite.


.. _IEEE754: https://en.wikipedia.org/wiki/IEEE_floating_point