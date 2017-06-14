.. _database:

==============
Banco de dados
==============

Também há suporte para micro esquema de banco de dados não-relacional.
Cada extensão pode armazenar um objeto JS que possa ser representado como JSON.
Esse objeto pode ser retornado juntamente com os alertas da extensão. Durante
a primeira execução, o valor sempre corresponde a ``undefined``.

**Exemplo de contador**

.. code-block:: javascript
   :emphasize-lines: 4, 8

   import { create } from 'rung-sdk';

   function main(context) {
       const counter = context.db === undefined ? 0 : context.db;

       return {
           alerts: [`The value is ${counter}`],
           db: counter + 1
       };
   }

   export default create(main, { params: {}, primaryKey: true };

Cada vez que a extensão roda, o contador é incrementado. Caso ele seja
``undefined``, é inicializado como ``0``. Você pode colocar objetos de
complexidade bem maiores dentro dele

Para mais informações sobre a utilização com o Rung CLI, visite db_.

.. _db: ../cli/db