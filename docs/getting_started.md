### Pré requisitos
- [Node.js / npm](https://nodejs.org/)

### Iniciando o projeto
#### Instalando o Rung Cli
O `rung-cli` está disponível como um pacote [`npm`](https://www.npmjs.com/package/rung-cli), para instalar globalmente execute o comando:
``` sh
npm install -g rung-cli
```
Caso queira verificar qual a versão do `rung-cli` instalado, execute:
```
rung --version
1.3.1
```
#### Boilerplate
Começar um projeto Rung é muito simples
```
rung boilerplate
```
Com o comando `boilerplate` pede algumas informações sobre o seu app e gera a base funcional de código para que você possa trabalha, mas não se preocupe, você poderá modifica-los posteriormente.

``` sh
? Project name "nome-do-app-rung"
? Version "1.0.0"
? Title "Título do app Rung"
? Description "Descrição completa do app"
? Category "Miscellaneous"
? license "MIT"
 ✔ Success: project generated
```
Segue descrição completa para cada uma das perguntas:

| Pergunta        | Descrição |
|-----------------|-----------|
| Nome do projeto | Identificador único do projeto, em caixa-baixa e separado por ``-`` |
| Versão          | Versão de acordo com o [semver](http://semver.org/) |
| Título          | Título do seu app para exibição na Rung App Store |
| Description     | Descrição humana da proposta do seu app |
| Category        | Identificador da categoria do seu app. Padrão: ``miscellaneous`` |
| Licença         | Licença em que seu app é distribuído. Padrão [MIT](https://opensource.org/licenses/MIT) |

Após confirmar, serão gerados ``package.json``, ``index.js``, ``info`` e ``README.md`` com as informações básicas de um app, conforme pode ser visto na imagem do VSCode abaixo.

![Projeto Rung no VSCode](https://i.imgur.com/zdvO2fN.png)

#### Executando um app
É possível testar os apps que desenvolve locamente sem a
necessidade de publicá-las para o Rung, mas antes de executar deverá ser instalado via `npm` as dependências do projeto com o comando:
```
npm install
```

Após isse execute `rung run` que criará uma interface visual que recebe os parâmetros de entrada
e mostrará o resultado obtido, os cartões que seriam gerados, para o
programador.

![Execução do rung-cli](https://i.imgur.com/Xtq4dJi.png)

#### Compilando um app

Você pode usar o comando ``rung build`` para compilar um app
para a forma binária, gerando um arquivo ``.rung``. O binário gerado
pode então ser usado para distribuição e publicação para a loja do Rung,
mas não precisa ser gerado para rodar um app localmente, levando
em conta que o *Rung CLI* consegue atuar diretamente como um interpretador.

O binário do Rung é uma forma modificada de um arquivo PKZip. Em tempo
de compilação, a VM do Rung executa seu app para garantir que não há
erros de análise do código exportado e gera os metadados para seu app
de forma estática, para otimizar a execução.

### Mais sobre o rung-cli
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
| `test`        | Runs the integration tests |

#### Options

| Option           | Description |
|------------------|-------------|
| `-o`, `--output` | Where to save the built package |
| `--version`      | Displays versions |
| `--private`      | If set, app is published for current user only |
| `--raw`          | Displays returned cards outside a table |
| `--live`         | With `run`, starts hot compiling and preview on browser |

#### Executando com locale customizado

Quando estiver testando internacionalização, pode forçar a definição
de um locale pelo próprio terminal, executando:

``RUNG_LOCALE=pt_BR rung run``

Por padrão, sem essa definição, o *Rung CLI* irá considerar o locale
padrão do seu sistema operacional.

#### Documentação do app

É possível usar o comando ``rung readme`` para gerar a documentação básica
para um app, incluindo informações sobre os parâmetros de entrada e
dinâmicas ([exemplo](https://github.com/rung-extensions/stock-exchange)).

