# Barra lateral personalizada

Usando a propriedade ``sidebar`` nas configurações, é possível escolher quais
campos deseja ocultar. Por padrão, a barra lateral possui suporte a 4 campos:


| Identificador | Descrição    |
|---------------|--------------|
| ``priority``  | Prioridade   |
| ``situation`` | Situação     |
| ``startDate`` | Data inicial |
| ``endDate``   | Data final   |

![Sidebar](../img/sidebar.png)

Se quisermos, por exemplo, remover os campos de data:

``` js
   export default create(main, {
       params,
       primaryKey: true,
       sidebar: {
           startDate: false,
           endDate: false
       }
   });
```

![Custom Sidebar](../img/custom-sidebar.png)