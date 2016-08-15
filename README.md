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

1. Pull `scripts.js` into `index.html` and reload page, verify log in console.

#### Using Redux (in console)

1. Pull redux into `index.html` using the cdn.
1. Initialize a redux store in your app in `scripts.js`

  ```js
  const { createStore } = Redux;
  ```
1. Give your store a reducer to use called `counter`

  ```js
  const store = createStore(counter);
  ```

1. Define counter above these constants

  ```js
  const counter = (state = 0, action) => {
    switch (action.type) {
      case 'INCREMENT':
        return state + 1;
      case 'DECREMENT':
        return state - 1;
      default:
        return state;
    };
  };
  ```

1. Verify your starting state of `0` (below all lines of code in `scripts.js` thus far):

  ```js
  console.log(store.getState());
  ```

1. Verify your incrementor is working (below all lines of code in `scripts.js` thus far):

  ```js
  store.dispatch({ type: 'INCREMENT'})
  console.log(store.getState());
  ```

  Feel free to also verify your decrementor.

#### Rendering to the page...

Now we want to put some stuff on the page so we can interact with the app instead of hardcoding in the console. We'll keep it simple here.

1. Remove all your console.logs from the `scripts.js` file, along with our hardcoded `store.dispatch` invocations.
1. We will need to wait for the document to finish loading before we read or make any changes on our document. All subsequent code will need to be inside:

  ```js
  window.onload = () => {

  }
  ```

1. We want to render the state to the page, so lets write a function that will do that, and call that function.

  ```js
  const render = () => {
    document.body.innerText = store.getState();
  };

  render();
  ```

  Now we can see our starting state of counter = 0 on the page.

1. Every time we click the page, we want to increment our counter. Add an event listener to `scripts.js`:

  ```js
  document.addEventListener('click', () =>{
    store.dispatch({ type: 'INCREMENT' });
  });
  ```

  If you add a `console.log('counter: ', store.getState())` within that event listener, you can see we are incrementing the counter, but it isn't changing the document...

1. We need to add a "change listener" to make sure that render is called any time state is changed... ([Check out the docs for `store.subscribe`](http://redux.js.org/docs/api/Store.html#subscribe))

  ```js
  store.subscribe(render);
  ```
