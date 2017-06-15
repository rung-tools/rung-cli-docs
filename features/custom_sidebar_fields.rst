.. _custom_sidebar_fields:

===========================
Barra lateral personalizada
===========================

Usando a propriedade ``sidebar`` nas configurações, é possível escolher quais
campos deseja ocultar. Por padrão, a barra lateral possui suporte a 4 campos:

+---------------+--------------+
| Identificador | Descrição    |
+===============+==============+
| ``priority``  | Prioridade   |
+---------------+--------------+
| ``situation`` | Situação     |
+---------------+--------------+
| ``startDate`` | Data inicial |
+---------------+--------------+
| ``endDate``   | Data final   |
+---------------+--------------+

.. image:: ../resources/sidebar.png

Se quisermos, por exemplo, remover os campos de data:

.. code-block:: javascript
   :emphasize-lines: 5, 6

   export default create(main, {
       params,
       primaryKey: true,
       sidebar: {
           startDate: false,
           endDate: false
       }
   });

.. image:: ../resources/custom-sidebar.png