# Express application generator

Use the **application generator tool**, `express-generator`, to quickly create an **application skeleton**.

You can run the **application generator** with the `npx` command (available in Node.js 8.2.0).

```text
$ npx express-generator
```

For earlier Node versions, install the application generator as a global npm package and then launch it:

```text
$ npm install -g express-generator
$ express
```

Display the command options with the `-h` option:

```text
$ express -h

  Usage: express [options] [dir]

  Options:

    -h, --help          output usage information
        --version       output the version number
    -e, --ejs           add ejs engine support
        --hbs           add handlebars engine support
        --pug           add pug engine support
    -H, --hogan         add hogan.js engine support
        --no-view       generate without view engine
    -v, --view <engine> add view <engine> support (ejs|hbs|hjs|jade|pug|twig|vash) (defaults to jade)
    -c, --css <engine>  add stylesheet <engine> support (less|stylus|compass|sass) (defaults to plain css)
        --git           add .gitignore
    -f, --force         force on non-empty directory
```

For example, the following creates an **Express app** named `myapp`. The **app** will be created in a folder named `myapp` in the **current working directory** and the **view engine** will be set to [Pug](https://pugjs.org/):

```text
$ express --view=pug myapp
```

Then **install dependencies**:

```text
$ cd myapp
$ npm install
```

On **MacOS** or **Linux**, *run the app* with this command:

```text
$ DEBUG=myapp:* npm start
```

On **Windows Command Prompt**, *run the app* with this command:

```text
> set DEBUG=myapp:* & npm start
```

**On Windows PowerShell**, *run the app* with this command:

```text
PS> $env:DEBUG='myapp:*'; npm start
```

Then load http://localhost:3000/ in your **browser** to **access the app**.

The **generated app** has the following **directory structure**:

```text
.
├── app.js
├── bin
│   └── www
├── package.json
├── public
│   ├── images
│   ├── javascripts
│   └── stylesheets
│       └── style.css
├── routes
│   ├── index.js
│   └── users.js
└── views
    ├── error.pug
    ├── index.pug
    └── layout.pug

7 directories, 9 files
```