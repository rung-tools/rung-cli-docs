## Criando uma nova integração

### Instalando o Rung Cli
``` sh
npm install -g rung-cli
```

#### Features

- Create blank extensions
- Generate `.rung` packages
- Run extensions locally in CLI mode
- Publish extensions to Rung Store (public and private)
- Generate boilerplate code for extension
- Generate README.md file to publish
- Test autocomplete directly in the terminal
- Hot reloading and live development

#### Usage

`rung [build|run|publish|boilerplate|readme|db]`

#### Commands


| Command       | Description |
|---------------|-------------|
| `build`       | Generate a .rung package |
| `run`         | Execute the current extension |
| `publish`     | Publish extension to store |
| `boilerplate` | Generate boilerplate code for the extension |
| `readme`      | Generate the README.md file to publish |
| `db read`     | Read from extension database |
| `db clear`    | Drop extension database |

#### Options

| Option           | Description |
|------------------|-------------|
| `-o`, `--output` | Where to save the built package |
| `--version`      | Displays versions |
| `--private`      | If set, extension is published for current user only |
| `--raw`          | Displays returned alerts outside a table |
| `--live`         | With `run`, starts hot compiling and preview on browser |



### Boilerplate

O comando ``rung boilerplate`` pede algumas informações sobre a sua extensão e gera a base funcional de código para que você possa trabalhar. Os parâmetros perguntados são:

| Pergunta        | Descrição |   
|-----------------|-----------| 
| Nome do projeto | Identificador único do projeto, em caixa-baixa e separado por ``-`` |
| Versão          | Versão de acordo com o [semver](http://semver.org/) |
| Título          | Título da sua extensão para exibição na Rung Store | 
| Description     | Descrição humana da proposta da sua extensão |
| Category        | Identificador da categoria da sua extensão. Padrão: ``miscellaneous`` |
| Licença         | Licença em que sua extensão é distribuída. Padrão [MIT](https://opensource.org/licenses/MIT) |

Após confirmar, serão gerados ``package.json``, ``index.js`` e ``README.md`` com as informações básicas de uma extensão.


### Documentação da extensão

É possível usar o comando ``rung readme`` para gerar a documentação básica
para uma extensão, incluindo informações sobre os parâmetros de entrada e
dinâmicas ([exemplo](https://github.com/rung-extensions/stock-exchange)).

