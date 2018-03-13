# Cartões personalizados

Além de texto plano, o Rung permite que os cartões possam ter um subset de HTML
personalizado para cada app. O compilador de apps do Rung possui
suporte direto a JSX, permitindo que o conceito do React seja aplicado aos
cartões em tempo de compilação.

![Custom cards](../img/custom-cards.png)

## JSX

Ao invés de definir o HTML como string, utilize-o diretamente na renderização.
Também há suporte a folha de estilos como objetos dentro das tags
Exemplo de app customizada:

``` js
import { create } from 'rung-sdk';

const styles = {
    name: {
        fontWeight: 'bold',
        color: 'red'
    }
};

function render(name) {
    return (
        <div>
            Hello, <span style={ styles.name }>{ name }</span>
        </div>
    );
}

function main(context) {
    return {
        cards: [{
            title: 'Betty',
            content: render('Betty')
        }]
    };
}

export default create(main, { params: {}, primaryKey: true });
```

## Preview

É ideal especificar como o cartão será exibido para o usuário durante a instalação
do app dentro do Rung App. Para isso, você pode definir nas configurações
o parâmetro ``preview`` e reutilizar a função ``render``:

``` diff
--- export default create(main, { params: {}, primaryKey: true });
+++ export default create(main, {
+    params: {},
+    primaryKey: true,
+    preview: render('Salete')
+});
```