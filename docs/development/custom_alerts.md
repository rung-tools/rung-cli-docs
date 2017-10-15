# Alertas personalizados

Além de texto plano, o Rung permite que os cards possam ter um subset de HTML
personalizado para cada extensão. O compilador de extensões do Rung possui
suporte direto a JSX, permitindo que o conceito do React seja aplicado aos
cards em tempo de compilação.

![Custom alerts](../img/custom-alerts.png)

## JSX

Ao invés de definir o HTML como string, utilize-o diretamente na renderização.
Também há suporte a folha de estilos como objetos dentro das tags
Exemplo de extensão customizada:

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
           alerts: [{
               title: 'Betty',
               content: render('Betty')
           }]
       };
   }

   export default create(main, { params: {}, primaryKey: true });
```

## Preview

É ideal especificar como o card será exibido para o usuário durante a instalação
da extensão dentro do Rung App. Para isso, você pode definir nas configurações
o parâmetro ``preview`` e reutilizar a função ``render``:

``` diff
   -export default create(main, { params: {}, primaryKey: true });
   +export default create(main, {
   +    params: {},
   +    primaryKey: true,
   +    preview: render('Salete')
   +});
```