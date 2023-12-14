# Jest Basics

Follow: [dev environment](dev_environment_000_about.md)


```
$ npm install @babel/core @babel/preset-env babel-loader --save-dev
$ npm install --save-dev jest
```


// babel.config.js
```js
module.exports = {
  presets: [['@babel/preset-env', {targets: {node: 'current'}}]],
};
```

// webpack.config.js
```js
  module: {  
    rules: [  
      {  
        test: /\.js$/,  
        exclude: /node_modules/,  
        use: {  
          loader: 'babel-loader',  
          options: {  
            presets: ['@babel/preset-env']  
          }  
        }  
      }  
    ]  
  }
```

https://jestjs.io/docs/getting-started

https://jestjs.io/docs/getting-started#using-babel (ideal)

https://jestjs.io/docs/webpack (webpack)


## How to

Cheatsheet: https://github.com/sapegin/jest-cheat-sheet

// sum.js
```js
function sum(a, b) {
  return a + b;
}
module.exports = sum;
```

// sum.test.js

```js
const sum = require('./sum');

test('adds 1 + 2 to equal 3', () => {
  expect(sum(1, 2)).toBe(3);
});
```


// package.json

add the following
```js
{
  "scripts": {
    "test": "jest"
  }
}
```

Finally, run:

```
$ npm test
```
