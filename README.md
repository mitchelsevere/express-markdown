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
│   └── dbqueries.js
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

_topic_ can be name based on whatever type of app you're building