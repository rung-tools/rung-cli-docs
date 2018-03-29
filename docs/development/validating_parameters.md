# Validação de parâmetros

Imaginemos os seguintes cenários:

> **Cenário 1**:
> João quer instalar um app que informa sobre o rastreamento de um objeto em uma determinada trasportadora.
> Ao preencher os parâmetros, João coloca um código de rastreio que não existe.

> **Cenário 2**:
> Maria decide instalar um app que avisa sobre promoções e quer ser avisada quando um home theater estiver em promoção, mas acaba escrevendo "home tiater" ao invés de "home theater".

Digamos que nestes dois apps, nenhum dos desenvolvedores lembrou de verificar se o código de rastreamento ou o termo de pesquisa eram válidos, e nestes casos, os apps nunca gerarão alertas, deixando os usuários esperando por algo que nunca vai acontecer.

Para evitar que isto aconteça, podemos fazer validações nos parâmetros e apresentar os erros de duas formas:
* Gerar um alerta dizendo que o código/termo é inválido
* Apresentar o erro no momento em que o usário clicar em "Salvar"

A primeira opção é simples, é apenas retornar um objeto na mesma estrutura de quando temos sucesso.

```js
return hasError
    ? { alerts: { 'error': { content: 'Código inválido.' } } }
    : { alerts }
```

Para a segunda forma, é necessário criar uma classe que extenda de "Error" e dar um "reject" nela, conforme o exemplo abaixo.

```js
class NotFoundError extends Error {
    constructor(message) {
        super(message);
        this.name = 'NotFoundError';
    }
}

function main(context) {
    const { code, description } = context.params;
    const { db } = context;
    const hasError = true;
    return hasError
        ? reject(new NotFoundError(_('Objeto não encontrado na base')))
        : { alerts }
}
```

O resultado pode ser visto abaixo.
![Exemplo de como seria exibido a mensagem de erro na validação dos parâmetros](../img/validation-error.png)