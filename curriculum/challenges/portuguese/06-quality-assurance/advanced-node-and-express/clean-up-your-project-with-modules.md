---
id: 589690e6f9fc0f352b528e6e
title: Limpar seu projeto com módulos
challengeType: 2
forumTopicId: 301549
dashedName: clean-up-your-project-with-modules
---

# --description--

Nesse momento, tudo que você tem é o seu arquivo `server.js`. Isso pode levar a dificuldades para gerenciar um código que não é muito expansível. Crie 2 arquivos novos: `routes.js` e `auth.js`

Ambos devem começar com o seguinte código:

```js
module.exports = function (app, myDataBase) {

}
```

Agora, no topo do arquivo do seu servidor, solicite estes arquivos assim: `const routes = require('./routes.js');` Depois disso, estabeleça uma conexão com o banco de dados, instanciando cada um dos arquivos da seguinte forma: `routes(app, myDataBase)`

Por fim, pegue todas as rotas do servidor, cole-as em seus novos arquivos e remova-as do arquivo do arquivo do servidor. Leve também a função `ensureAuthenticated`, já que ela foi especificamente criada para o roteamento. Agora, você precisará adicionar corretamente as dependências em que são usadas, tais como `const passport = require('passport');`, no topo do arquivo, acima da linha de exportação do arquivo `routes.js`.

Continue adicionando-os até que não existam mais erros e que o arquivo do servidor não tenha mais nenhuma rota (**exceto a rota no bloco catch**)!

Do the same thing in your `auth.js` file with all of the things related to authentication such as the serialization and the setting up of the local strategy and erase them from your server file. Certifique-se de adicionar as dependências e de chamar `auth(app, myDataBase)` no servidor no mesmo local.

Envie sua página quando você achar que ela está certa. If you're running into errors, you can <a href="https://forum.freecodecamp.org/t/advanced-node-and-express/567135#clean-up-your-project-with-modules-2" target="_blank" rel="noopener noreferrer nofollow">check out an example of the completed project</a>.

# --hints--

Os módulos devem estar presentes.

```js
async (getUserInput) => {
  const url = new URL("/_api/server.js", getUserInput("url"));
  const res = await fetch(url);
  const data = await res.text();
  assert.match(
    data,
    /require\s*\(('|")\.\/routes(\.js)?\1\)/gi,
    'You should have required your new files'
  );
  assert.match(
    data,
    /client\s*\.db[^]*routes/gi,
    'Your new modules should be called after your connection to the database'
  );
}
```

# --solutions--

```js
/**
  Backend challenges don't need solutions, 
  because they would need to be tested against a full working project. 
  Please check our contributing guidelines to learn more.
*/
```
