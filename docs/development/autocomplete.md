# AutoComplete

O Rung suporta que os campos possam ter a função de autocompletar, provendo
uma função JavaScript que lida com o retorno baseado na entrada.

Para que um campo seja autocompletável, é necessário defini-lo como um campo
do tipo ``AutoComplete``, disponível em ``rung-cli/dist/types``.

Vamos criar um campo que tenha o autocompletar com nomes de Pokémons nesse
exemplo!

- Defina o tipo do campo como ``AutoComplete``

``` js
   params: {
       pokemon: {
           type: AutoComplete,
           description: 'Pick a Pokémon!'
       }
   }
```

- Crie um arquivo ``autocomplete/pokemon.js``
- Exporte uma função que use a função de *callback* ou que retorne uma lista de strings

``` js
   export default function ({ input, lib }) {
        return lib.request.get('https://raw.githubusercontent.com/BrunnerLivio/PokemonDataGraber/master/output.json')
           .then(({ text }) => JSON.parse(text))
           .then(pokemons => pokemons.map(pokemon => pokemon.Name))
           .filter(name => name.startsWith(input));
   }
```
E pronto, compile e suba sua extensão para o Rung! Você também pode testar essa funcionalidade
na sua extensão diretamente do Rung CLI (automaticamente).

## Parâmetros

A função exportada recebe como parâmetros:

1. Objeto contendo ``input`` (entrada do usuário) e ``lib``
2. Callback opcional ``done``. Se passado, deve ser chamado para retornar o controle. Senão, a função deve retornar uma ``Promise``

## Retorno

``Promise`` ou chamada de ``done`` a um ``Array<String>`` contendo os dados já filtrados.

## Bibliotecas

O parâmetro ``lib`` vindo dentro do primeiro objeto carrega duas bibliotecas, ``ramda`` e ``request``.
As requisições são feitas utilizado a biblioteca externa ``superagent``.
