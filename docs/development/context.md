# Contexto

O contexto é o primeiro parâmetro passado para a função principal da sua
extensão. Ele traz informações importantes, como o locale do usuário e os
valores dos parâmetros que são informados.

Exemplo:

```js
   import { create } from 'rung-sdk';
   import { Integer } from 'rung-sdk/dist/types';

   function main(context) {
       const { a, b } = context.params;

       return {
           alerts: [`Sum of ${a} and ${b} is ${a + b}`]
       };
   }

   const params = {
       a: {
           description: 'First number',
           type: Integer
       },
       b: {
           description: 'Second number',
           type: Integer
       }
   };

   export default create(main, { params });
```

O contexto também é responsável por carregar as informações do banco de dados
de cada instância de extensão, em ``context.db``.