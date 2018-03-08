## Criando um novo app

### Instalando o Rung Cli
``` sh
npm install -g rung-cli
```

#### Features

- Create blank apps
- Generate `.rung` packages
- Run apps locally in CLI mode
- Publish apps to Rung App Store (public and private)
- Generate boilerplate code for app
- Generate README.md file to publish
- Test autocomplete directly in the terminal
- Hot reloading and live development

#### Usage

`rung [build|run|publish|boilerplate|readme|db]`

#### Commands


| Command       | Description |
|---------------|-------------|
| `build`       | Generate a .rung package |
| `run`         | Execute the current app |
| `publish`     | Publish app to store |
| `boilerplate` | Generate boilerplate code for the app |
| `readme`      | Generate the README.md file to publish |
| `db read`     | Read from app database |
| `db clear`    | Drop app database |

#### Options

| Option           | Description |
|------------------|-------------|
| `-o`, `--output` | Where to save the built package |
| `--version`      | Displays versions |
| `--private`      | If set, app is published for current user only |
| `--raw`          | Displays returned cards outside a table |
| `--live`         | With `run`, starts hot compiling and preview on browser |



### Boilerplate

O comando ``rung boilerplate`` pede algumas informações sobre o seu app e gera a base funcional de código para que você possa trabalhar. Os parâmetros perguntados são:

| Pergunta        | Descrição |
|-----------------|-----------|
| Nome do projeto | Identificador único do projeto, em caixa-baixa e separado por ``-`` |
| Versão          | Versão de acordo com o [semver](http://semver.org/) |
| Título          | Título do seu app para exibição na Rung App Store |
| Description     | Descrição humana da proposta do seu app |
| Category        | Identificador da categoria do seu app. Padrão: ``miscellaneous`` |
| Licença         | Licença em que seu app é distribuído. Padrão [MIT](https://opensource.org/licenses/MIT) |

Após confirmar, serão gerados ``package.json``, ``index.js`` e ``README.md`` com as informações básicas de um app.


### Documentação do app

É possível usar o comando ``rung readme`` para gerar a documentação básica
para um app, incluindo informações sobre os parâmetros de entrada e
dinâmicas ([exemplo](https://github.com/rung-extensions/stock-exchange)).

