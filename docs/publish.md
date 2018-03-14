# Publicando seu app

Após o desenvolvimento, podemos publicar o app para a Rung App Store. O
Rung CLI implementa o comando ``rung publish`` para isso. Ao publicar um app, informe seu usuário e senha do Rung.

Você também poderá realizar o procedimento diretamente no [portal do desenvolvedor Rung](https://developers.rung.com.br)

![Publicando app no Rung Developers](https://i.imgur.com/rKveAJ5.png)

## Restrições de publicação

- A versão deve atender ao [semver](http://semver.org/);
- Ao atualizar um app, a versão deve ser incrementada;
- É necessário possuir *karma* de desenvolvedor.

Para conseguir *karma* de publicação, você deverá ter um cadastro no [portal do desenvolvedor Rung](https://developers.rung.com.br)

Para publicar um app, é obrigatório que ``title`` e ``description``
estejam definidos na configuração do app.