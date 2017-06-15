.. _boilerplate:

O comando ``rung boilerplate`` pede algumas informações sobre a sua extensão
e gera a base funcional de código para que você possa trabalhar. Os parâmetros
perguntados são:

+-----------------+-----------------------------------------------------------------------+
| Pergunta        | Descrição                                                             |
+=================+=======================================================================+
| Nome do projeto | Identificador único do projeto, em caixa-baixa e separado por ``-``   |
+-----------------+-----------------------------------------------------------------------+
| Versão          | Versão de acordo com o semver_                                        |
+-----------------+-----------------------------------------------------------------------+
| Título          | Título da sua extensão para exibição na Rung Store                    |
+-----------------+-----------------------------------------------------------------------+
| Description     | Descrição humana da proposta da sua extensão                          |
+-----------------+-----------------------------------------------------------------------+
| Category        | Identificador da categoria da sua extensão. Padrão: ``miscellaneous`` |
+-----------------+-----------------------------------------------------------------------+
| Licença         | Licença em que sua extensão é distribuída. Padrão MIT_                |
+-----------------+-----------------------------------------------------------------------+

Após confirmar, serão gerados ``package.json``, ``index.js`` e ``README.md``
com as informações básicas de uma extensão.

.. _semver: http://semver.org/
.. _MIT: https://opensource.org/licenses/MIT