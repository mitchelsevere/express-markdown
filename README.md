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