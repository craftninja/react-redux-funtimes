# README

### how did you make this lovely thing? (aka notes on building)

#### basic setup, initial commit

1. `$ mkdir <NAME>`, `$ cd <NAME>`, `$ git init`, `$ touch README.md`
1. Open project in editor of choice and take notes on building in `README.md`
1. `touch index.html` with following content:

  ```html
  <!DOCTYPE html>
  <html>
    <head>
      <meta charset="utf-8">
      <title>ReactRedux</title>
    </head>
    <body>

    </body>
  </html>
  ```

1. `$ npm init -y`
1. if `http-server` is not installed(`$ http-server --help` should return some usage):
  * `$ npm install -g http-server`
1. in `package.json`, change `test` script to `start` script:
  * `http-server -c-1 -o`
  * `-c-1` - cache flag with neg 1 means never cache your files
  * `-o` - open up in your browser
1. `$ npm start`
1. `touch scripts.js` with the following content

  ```js
  console.log('shit is wired up')
  ```

1. Pull scripts into `index.html` and reload page, verify log in console.
