# Express Markdown
### File Structure for Express MVC Application

```bash
├── README.md
├── app.js
├── controllers
│   └── controller.js
├── db
│   ├── config.js
│   ├── migrations
│       └── migrations.sql
│   └── seeds
│       ├── database.sql
│       └── seed.sql
├── models
│   └── topic.js
├── node_modules
├── package.json
├── public
│   ├── src
│   │   └── main.js
│   └── styles
│       ├── reset.css
│       └── style.css
├── routes
│   └── routes.js
└── views
    ├── partials
    │   ├── head.ejs (or boilerplate.ejs)
    │   └── end.ejs
    ├── index.ejs
    └── topic
        ├── topic-edit.ejs
        ├── topic-index.ejs
        ├── topic-new.ejs
        └── topic-single.ejs
```

_topic_ can be named based on whatever type of app you're building

#### Part 1: Setup
```
NPM
1. npm init
2. npm install --save express
3. npm install --save morgan
4. npm install --save body-parser
5. npm install --save pg-promise

Optional
npm install -g nodemon
```

```
START SCRIPTS
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node app.js",
    "dev": "nodemon app.js",
    "debugger": "DEBUG=*:* npm run dev"
  }
```

#### Part 2: Databases
Run database migration and schema / seed files
```js
// inside the migration folder
psql -f [migration-name].sql 

// inside the seeds folder
psql -f seed.sql
```
Set up config file for database queries
```
const options = {
  query: (e) => {
    console.log(e.query);
  }
};

const pgp = require('pg-promise')(options);

const db = (() => {
  if (process.env.NODE_ENV === 'development' || !process.env.NODE_ENV) {
    return pgp({
      database: 'pizza_delorean_dev',
      port: 5432,
      host: 'localhost',
    });
  } else if (process.env.NODE_ENV === 'production') {
    return pgp(process.env.DATABASE_URL);
  }
})();

module.exports = db;
```

#### Part 3: App.js setup
```js
// 1a. require dependencies
const express = require('express');
const logger = require('morgan');
const path = require('path');
const bodyParser = require('bodyParser')
// 1b. initialize express and port
const app = express();
const port = process.env.PORT || 3000;
// 4. middleware
app.use(logger('dev)); 
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({extended: false}));
// 5a. static directory
app.use(express.static('public'));
// 5b. where to find views directory
app.set('views', path.join(__dirname, 'views'));
app.set('view engine', 'ejs');
// 2. have express instance listen on port
app.listen(port, () => {
    console.log('Listening on port', port);
});
// 3a. use res.send to test if root and server are working properly
app.get('/', (req, res) => {
    res.send('Hello world!');
});
// 3b. error catch all (must be at the bottom of the file)
app.get('*', (req, res) => {
    res.status(404).send('Not found');
});
```
