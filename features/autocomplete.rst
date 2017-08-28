.. _autocomplete:

============
Autocomplete
============

O Rung suporta que os campos possam ter a função de autocompletar, provendo
uma função JavaScript que lida com o retorno baseado na entrada.

Para que um campo seja autocompletável, é necessário defini-lo como um campo
do tipo ``Autocomplete``, disponível em ``rung-cli/dist/types``.

Vamos criar um campo que tenha o autocompletar com nomes de Pokémons nesse
exemplo!

- Defina o tipo do campo como ``Autocomplete``

.. code-block:: javascript

   params: {
       pokemon: {
           type: Autocomplete,
           description: 'Pick a Pokémon!'
       }
   }

- Crie um arquivo ``autocomplete/pokemon.js``
- Exporte uma função que use a função de *callback* ou que retorne uma lista de strings

.. code-block:: javascript

   export default function ({ input, lib }, done) {
       lib.request.get('https://raw.githubusercontent.com/BrunnerLivio/PokemonDataGraber/master/output.json')
           .then(res => res.body)
           .then(pokemons => pokemons.map(pokemon => pokemon.Name))
           .filter(name => name.startsWith(input))
           .then(done);
   }

E pronto, compile e suba sua extensão para o Rung!
