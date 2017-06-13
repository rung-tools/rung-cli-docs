.. _run:

=======================
Executando uma extensão
=======================

É possível testar as extensões que desenvolve locamente sem a
necessidade de publicá-las para o Rung. O *Rung CLI* provê o comando
``rung run`` para isso.

.. image:: ../resources/run.png

É criada uma interface visual que recebe os parâmetros de entrada
e mostra o resultado obtido, os alertas que seriam gerados, para o
programador.

---------------------------------
Executando com locale customizado
---------------------------------

Quando estiver testando internacionalização, pode forçar a definição
de um locale pelo próprio terminal, executando:

``RUNG_LOCALE=pt_BR rung run``

Por padrão, sem essa definição, o *Rung CLI* irá considerar o locale
padrão do seu sistema operacional.