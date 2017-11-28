# Tipos de parâmetros

Os parâmetros de entrada de uma extensão do Rung possuem diversos tipos com
múltiplas finalidades, que variam de acordo com como você vai trabalhar com
o dado e como você deseja que ele seja renderizado para o usuário durante
a instalação. Os tipos podem ser importados via:

``` js
import {} from 'rung-cli/dist/types';
```
## Tipos


### AutoComplete

Para campos que podem ser interdependentes, em modo texto e ter um arquivo expondo uma função de *autocomplete*.

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

#### Parâmetros

A função exportada recebe como parâmetros:

1. Objeto contendo ``input`` (entrada do usuário) e ``lib``
2. Callback opcional ``done``. Se passado, deve ser chamado para retornar o controle. Senão, a função deve retornar uma ``Promise``

#### Retorno

``Promise`` ou chamada de ``done`` a um ``Array<String>`` contendo os dados já filtrados.

#### Bibliotecas

O parâmetro ``lib`` vindo dentro do primeiro objeto carrega duas bibliotecas, ``ramda`` e ``request``.
As requisições são feitas utilizado a biblioteca externa ``superagent``.


### Integer

Para números inteiros tendendo de negativo a infinito positivo, a depender da
representação de números inteiros em bits de onde está rodando.

### Double

Para números de ponto flutuante (decimais), a depender da representação de
números de ponto flutuante em bits de onde está rodando, geralmente segundo
a [IEEE754](https://en.wikipedia.org/wiki/IEEE_floating_point).

### DateTime

*Indisponível*

### Natural

Números naturais de 0 a infinito. Não são aceitos números negativos

### Char(n)

Textos de até ``n`` caracteres, onde ``n`` corresponde a um número natural.
Se tiver como entrada um texto maior, este é cortado até o limite.

### IntegerRange(m, n)

Intervalos numéricos de números inteiros entre ``m`` e ``n``. É possível, por
exemplo, simular números naturais com ``IntegerRange(0, Infinity)``. ``m``
sempre precisa ser menor do que ``n`` para que haja uma situação válida.

### DoubleRange(m, n)

Intervalos numéricos de números de ponto flutuante (decimais) entre ``m`` e
``n``, onde ``m`` precisa ser um valor menor que ``n``.

### Money

*Indisponível*

### String

Qualquer trecho de texto arbitrário

### Color

Cor em hexadecimal, começando por `#`.

### Email

Qualquer email válido.

### Checkbox

*Indisponível*

### OneOf(xs)

Qualquer elemento de ``xs``, onde ``xs`` deve ser do tipo ``string[]`` (lista
de strings).

### Url

Url independente de protocolo (HTTP, FTP ...).

### IntegerMultiRange(m, n)

Slider em que 2 pontos são retornados, estão esses pontos entre ``m`` e ``n``.

### Calendar

Para datas, com renderização de um calendário.

### Location

Qualquer trecho de texto que faça referência a uma localização (cidade, estabelecimento, país, etc). Quando o campo for utilizado no [Rung](https://app.rung.com.br), irá ser carregado um autocomplete com sugestões de locais vindas do [Google](https://developers.google.com/maps/documentation/javascript/examples/places-autocomplete-addressform).
