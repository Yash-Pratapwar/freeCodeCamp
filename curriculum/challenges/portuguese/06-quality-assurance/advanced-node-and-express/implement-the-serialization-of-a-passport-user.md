---
id: 5895f70cf9fc0f352b528e67
title: Implementar a serialização de um usuário do Passport
challengeType: 2
forumTopicId: 301556
dashedName: implement-the-serialization-of-a-passport-user
---

# --description--

You are not loading an actual user object since the database is not set up. Connect to the database once, when you start the server, and keep a persistent connection for the full life-cycle of the app. To do this, add your database's connection string (for example: `mongodb+srv://<username>:<password>@cluster0-jvwxi.mongodb.net/?retryWrites=true&w=majority`) to the environment variable `MONGO_URI`. Este é usado no arquivo `connection.js`.

*If you are having issues setting up a free database on MongoDB Atlas, check out this <a href="https://www.freecodecamp.org/news/get-started-with-mongodb-atlas/" target="_blank" rel="noopener noreferrer nofollow">tutorial</a>.*

Now you want to connect to your database, then start listening for requests. The purpose of this is to not allow requests before your database is connected or if there is a database error. To accomplish this, encompass your serialization and app routes in the following code:

```javascript
myDB(async client => {
  const myDataBase = await client.db('database').collection('users');

  // Be sure to change the title
  app.route('/').get((req, res) => {
    // Change the response to render the Pug template
    res.render('index', {
      title: 'Connected to Database',
      message: 'Please login'
    });
  });

  // Serialization and deserialization here...

  // Be sure to add this...
}).catch(e => {
  app.route('/').get((req, res) => {
    res.render('index', { title: e, message: 'Unable to connect to database' });
  });
});
// app.listen out here...
```

Certifique-se de descomentar o código `myDataBase` em `deserializeUser` e de editar o seu `done(null, null)` para incluir o `doc`.

Envie sua página quando você achar que ela está certa. If you're running into errors, you can <a href="https://forum.freecodecamp.org/t/advanced-node-and-express/567135#implement-the-serialization-of-a-passport-user-5" target="_blank" rel="noopener noreferrer nofollow">check out the project completed up to this point</a>.

# --hints--

A conexão do banco de dados deve estar presente.

```js
async (getUserInput) => {
  const url = new URL("/", getUserInput("url"));
  const res = await fetch(url);
  const data = await res.text();
  assert.match(
    data,
    /Connected to Database/gi,
    'You successfully connected to the database!'
  );
}
```

A desserialização agora deve estar usando corretamente o banco de dados e `done(null, null)` deve ser chamado com o `doc`.

```js
async (getUserInput) => {
  const url = new URL("/_api/server.js", getUserInput("url"));
  const res = await fetch(url);
  const data = await res.text();
  assert.match(
    data,
    /null,\s*doc/gi,
    'The callback in deserializeUser of (null, null) should be altered to (null, doc)'
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
