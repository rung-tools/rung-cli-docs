.. _build:

=======================
Compilando uma extensão
=======================

Você pode usar o comando ``rung build`` para compilar uma extensão
para a forma binária, gerando um arquivo ``.rung``. O binário gerado
pode então ser usado para distribuição e publicação para a loja do Rung,
mas não precisa ser gerado para rodar uma extensão localmente, levando
em conta que o *Rung CLI* consegue atuar diretamente como um interpretador.

O binário do Rung é uma forma modificada de um arquivo PKZip. Em tempo
de compilação, a VM do Rung executa sua extensão para garantir que não há
erros de análise do código exportado e gera os metadados para sua extensão
de forma estática, para otimizar a execução.

