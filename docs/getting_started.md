## Criando uma nova integração

bla bla bla

### Instalando o Rung Cli
bla bla bla bla bla bla
``` sh
npm install -g rung-cli
rung boilerplate
```


## Features

- Create blank extensions
- Generate `.rung` packages
- Run extensions locally in CLI mode
- Publish extensions to Rung Store (public and private)
- Generate boilerplate code for extension
- Generate README.md file to publish
- Test autocomplete directly in the terminal
- Hot reloading and live development

## Usage

`rung [build|run|publish|boilerplate|readme|db]`

### Commands


| Command       | Description |
|---------------|-------------|
| `build`       | Generate a .rung package |
| `run`         | Execute the current extension |
| `publish`     | Publish extension to store |
| `boilerplate` | Generate boilerplate code for the extension |
| `readme`      | Generate the README.md file to publish |
| `db read`     | Read from extension database |
| `db clear`    | Drop extension database |

### Options

| Option           | Description |
|------------------|-------------|
| `-o`, `--output` | Where to save the built package |
| `--version`      | Displays versions |
| `--private`      | If set, extension is published for current user only |
| `--raw`          | Displays returned alerts outside a table |
| `--live`         | With `run`, starts hot compiling and preview on browser |