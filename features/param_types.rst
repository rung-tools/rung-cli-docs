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


**Utilização**

.. code-block::javascript

    Integer


Para números inteiros tendendo de negativo a infinito positivo, a depender da
representação de números inteiros em bits de onde está rodando