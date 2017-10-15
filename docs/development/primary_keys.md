# Chaves primárias

Cada alerta pode ter uma chave primária. A chave primária serve para localizar
aquele alerta e o preservar em uma atualização. É indiciado que todo alerta
possua uma chave primária para que seus metadados não sejam perdidos durante
cada execução da extensão.

Para habilitar o suporte às chaves primárias, deve-se utilizar o segundo
parâmetro da função ``create`` da SDK do Rung:

```js
export default create(main, {
    params,
    primaryKey: true
});
```

Por padrão, os alertas devem ser retornados em um objeto contendo
``{ alerts }``. Nessa situação, ``alerts`` deve conter um objeto ou *array*
com as chaves e os valores de cada alerta. No caso de um *array*, a chave
utilizada será o índice. Com ES6, você pode construir um objeto com chaves
dinâmicas utilizando a sintaxe ``{ [key]: value }``. Exemplo:

``` js
import { map, mergeAll } from 'ramda';

function render({ id, name, score }) {
    return { [id]: `${name} with ${score} points!` };
}

function main(context) {
    const students = [
        { id: '0001', name: 'Bianca del Rio', score: 8 },
        { id: '0002', name: 'Violet Chachki', score: 9 },
        { id: '0003', name: 'Dida Ritz', score: 3 }
    ];

    return {
        alerts: mergeAll(map(render, students))
    };
}

export default create(main, { params: {}, primaryKey: true });
```