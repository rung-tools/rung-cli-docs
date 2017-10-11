.. _live:

=============
Hot reloading
=============

A partir da versão ``1.1.1``, o Rung CLI suporta desenvolvimento agilizado através de edição ao
vivo e compilação dinâmica. Se você está habituado a desenvolver com React, vai se sentir
familiarizado.

.. image:: ../resources/live-preview.png

---------------
Como configurar
---------------

Para habilitar o modo ``live``, rode sua extensão com ``rung run --live``, e preencha os valores
dos parâmetros de entrada. Nada mais é necessário. O Rung CLI irá monitorar as mudanças e
compilar dinamicamente!

.. image:: ../resources/live-console.png

--------------
Linha do tempo
--------------

Como o estado é puro, uma linha do tempo é criada e você pode navegar pelos estados anteriores.
Quando uma mudança é detectada, uma nova era é criada e a aplicação é reposicionada para ela.

.. image:: ../resources/live-timeline.png

-----
Erros
-----

Erros sintáticos e de *runtime* serão exibidos em uma caixa específica.

.. image:: ../resources/live-error.png

-------------
Barra lateral
-------------

Você pode clicar nos alertas para ver o resultado da renderização do *markdown* para comentários
na barra lateral.

