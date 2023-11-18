# About Dev Environemnt

https://peterxjang.com/blog/modern-javascript-explained-for-dinosaurs.html

## NPM

Node Package Manager

<details>
        <summary>NPM</summary>

Instead of needing to install `moment.min.js` (example) into the filesystem like so  
```html
<!-- index.html -->  
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <title>Example</title>  
  <link rel="stylesheet" href="index.css">  
  <script src="./moment.min.js"></script>
  <script src="./script.js"></script>  
</head>  
<body>  
  <h1>Hello from HTML!</h1>  
</body>  
</html>
```

So that in `script.js` you could do:

```js
// script.js  
console.log("Hello from JavaScript!");  
console.log(moment().startOf('day').fromNow()); // <-
```

Which is problematic because you had to always manually reinstall the latest `moment.min.js` anytime there was an upgrade (and find the repo and such)



---

We can use instead a package manager which automates this for us

`$ npm init`

creates a package.json (a configuration file that npm uses to save all project information). Looks something like:
```json
{  
  "name": "your-project-name",  
  "version": "1.0.0",  
  "description": "",  
  "main": "index.js",  
  "scripts": {  
    "test": "echo \"Error: no test specified\" && exit 1"  
  },  
  "author": "",  
  "license": "ISC"  
}
```

To install the moment.js JavaScript package, we can now follow the npm instructions from their home page by entering the following command in the command line:

`$ npm install moment --save`

This command does two things — first, it downloads all the code from the moment.js package into a folder called node_modules. Second, it automatically modifies the package.json file to keep track of moment.js as a project dependency.

```json
{  
  "name": "modern-javascript-example",  
  "version": "1.0.0",  
  "description": "",  
  "main": "index.js",  
  "scripts": {  
    "test": "echo \"Error: no test specified\" && exit 1"  
  },  
  "author": "",  
  "license": "ISC", 
  
  
  "dependencies": {  
    "moment": "^2.22.2"  
  } 

}
```
This is useful later when sharing a project with others — instead of sharing the `node_modules` folder (which can get very large), you only need to share the `package.json file` and other developers can install the required packages automatically with the command `npm install`.

---

And now

```html
<!-- index.html -->  
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <title>JavaScript Example</title>  
  <script src="./node_modules/moment/min/moment.min.js"></script>
  <script src="./scirpt.js"></script>  
</head>  
<body>  
  <h1>Hello from HTML!</h1>  
</body>  
</html>
```

</details>

<details>
        <summary>Package.json</summary>

`$ npm init --yes`

Wrote to /home/monatheoctocat/my_package/package.json:

```json


{
  "name": "my_package",
  "description": "",
  "version": "1.0.0",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "https://github.com/monatheoctocat/my_package.git"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "bugs": {
    "url": "https://github.com/monatheoctocat/my_package/issues"
  },
  "homepage": "https://github.com/monatheoctocat/my_package"
}
```

Default values extracted from the current directory

-  `name`: the current directory name
-  `version`: always `1.0.0`
-  `description`: info from the README, or an empty string `""`
-  `scripts`: by default creates an empty `test` script
-  `keywords`: empty
-  `author`: empty
-  `license`: `ISC`
-  `bugs`: information from the current directory, if present
-  `homepage`: information from the current directory, if present


</details>

## Webpack

JavaScript module bundler

<details>
        <summary>Webpack</summary>

Instead of needing to do :

```html
<!-- index.html -->  
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <title>JavaScript Example</title>  
  <script src="./node_modules/moment/min/moment.min.js"></script> <!-- this -->
  <!-- And again for all the packages we have -->
  <script src="./scirpt.js"></script>  
</head>  
<body>  
  <h1>Hello from HTML!</h1>  
</body>  
</html>
```

We would like to have instead just something like this:

```js
// script.js  
var moment = require('moment'); // <-
console.log("Hello from JavaScript!");  
console.log(moment().startOf('day').fromNow());
```

Installing webpack (a node package):

`$ npm install webpack webpack-cli --save-dev`

> Note: We’re installing two packages — webpack and webpack-cli (which enables you to use webpack from the command line) into the `node_modules` folder. In the `package.json` you'll see our new dev dependencies:

```json
{  
  "name": "modern-javascript-example",  
  "version": "1.0.0",  
  "description": "",  
  "main": "index.js",  
  "scripts": {  
    "test": "echo \"Error: no test specified\" && exit 1"  
  },  
  "author": "",  
  "license": "ISC",  
  "dependencies": {  
    "moment": "^2.19.1"  
  },


  "devDependencies": {  
    "webpack": "^4.17.1",  
    "webpack-cli": "^3.1.0"  
  }


}
```

To run the webpack tool:

`$ ./node_modules/.bin/webpack index.js --mode=development`

It starts with the `./script.js` file, finds any `require` statements, and replaces them with the appropriate code to create a single output file (which by default is **`dist/main.js`**). 

Now that we have webpack’s **`dist/main.js`** output, we are going to use it instead of `./script.js` in the browser. This would be reflected in the `index.html `file as follows:

```html
<!-- index.html -->  
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <title>JavaScript Example</title>  
  <script src="dist/main.js"></script>
</head>  
<body>  
  <h1>Hello from HTML!</h1>  
</body>  
</html>
```

---

Note that we’ll need to run the webpack command each time we change `script.js`. This is tedious, and will get even more tedious as we use webpack’s more advanced features. Webpack can read options from a config file in the root directory of the project named `webpack.config.js`, which in our case would look like:

```js
// webpack.config.js  
module.exports = {  
  mode: 'development',  
  entry: './script.js',  
  output: {  
    filename: 'main.js',  
    publicPath: 'dist'  
  }  
};
```

Now each time we change `script.js`, we can run webpack with the command:

`$ ./node_modules/.bin/webpack`

</details>

Setup: https://webpack.js.org/

And generally: https://webpack.js.org/guides/getting-started/

## Babel

Transpiling code for new language features

<details>
        <summary>Babel</summary>

Transpiling code means converting the code in one language to code in another similar language. Examples of similar languages:

- CSS -> Sass, Less, and Stylus
- JS -> CoffeeScript, Babel, TypeScript

**Babel** is not a new language but a transpiler that transpiles next generation JavaScript with features not yet available to all browsers (ES2015 and beyond) to older more compatible JavaScript (ES5).

---

Installing Babel (a node package)

`$ npm install @babel/core @babel/preset-env babel-loader --save-dev`

> Note: We’re installing 3 separate packages as dev dependencies 
>
> 1.  `@babel/core` is the main part of babel
> 2.  `@babel/preset-env` is a preset defining which new JavaScript features to transpile
> 3.  `babel-loader` is a package to enable babel to work with **webpack**

We can configure webpack to use babel-loader by editing the `webpack.config.js` file as follows:

```js
// webpack.config.js  
module.exports = {  
  mode: 'development',  
  entry: './index.js',  
  output: {  
    filename: 'main.js',  
    publicPath: 'dist'  
  },  


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


};
```

Basically we’re telling webpack to look for any `.js` files (excluding ones in the `node_modules` folder) and apply babel transpilation using `babel-loader` with the `@babel/preset-env` preset. 

Now we can use **ES2015 features** in js
```js
// for example:
let name = "Bob", time = "today";  
console.log(`Hello ${name}, how are you ${time}?`);
// or
import moment from 'moment';
```

---

Since we changed script.js, we need to run webpack again in the command line:

`$ ./node_modules/.bin/webpack`

</details>

## ES6 Modules

### Export

```js
// a file called myModule.js
const functionOne = () => 'ONE';
const functionTwo = () => 'TWO';

export {
  functionOne,
  functionTwo
};
```

### Import

```js
// index.js in /src folder
import {functionOne, functionTwo} from './myModule';

functionOne(); // this should work as expected!
functionTwo(); // this should work as expected!
```

## Using Them Together

1. Go to project directory and do:

    - `$ npm init`

> It will generate a `package.json`

2. Inside `packag.json` change `"main": "index.js",` to `"private": true,`. So as to avoid accidental publishing of code

3. Get webpack there:

    - `$ npm init -y`

    - `$ npm install webpack webpack-cli --save-dev`

4. Add a `.gitignore` file. And inside it write:
```
node_modules
```

5. Create a `src` and `dist` directory

    - Create `src/index.js`
    - Create `dist/index.html`

6. In `src/index.js` add `<script src="main.js"></script>` inside the `body` tag at the end

7. Create a `webpack.config.js` in it write the following:

```js
const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'main.js',
    path: path.resolve(__dirname, 'dist'),
  },
};
```

8. (Fill `dist/index.html` and `src/index.js`)

9. Get packages `npm install --save <some package>`. And then in `src/index.js` at top write `import <thing you're importing> from '<some package>';`

10. Run `$ npx webpack`

> If you run `$ npx webpack --watch` you will not have to rerun webpack every time you make a change.

11. Make an NPM script. Go to `package.json` and change the `"scripts` to have a `"build"` of `"webpack"`:

```json
"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1",
  "build": "webpack"
},
```

> Allows you to do `$ npm run build`

Project should look like:
```
webpack-demo
|- package.json
|- package-lock.json
|- webpack.config.js
|- /dist
  |- main.js
  |- index.html
|- /src
  |- index.js
|- /node_modules
```

12. If you get tired of doing `$ npm run build` everytime you make a change then follow: https://webpack.js.org/guides/development/#using-watch-mode

> Note: if you use `webpack-dev-server` and decide to use `HTML Webpack Plugin` then instead of running from `static: './dist',` you need to change it to `static: './src',`

> `webpack-dev-middleware` uses Express. (You'll probably just want `webpack-dev-server`)

### HTML Webpack Plugin

Automatically build an HTML file in `dist` for us when we build our project. It will also then automatically add certain things to the HTML like our output bundle in a `<script>` tag, or the code to use a favicon if we configured it to use one.

1. `$ npm install --save-dev html-webpack-plugin`

2. Add to `webpack.config.js`:

```js
// webpack.config.js

const HtmlWebpackPlugin = require('html-webpack-plugin');

// Inside module.exports = {...
  // ...
  plugins: [
      new HtmlWebpackPlugin({
          template: './src/template.html',
      }),
  ],
  // ...
// }
```

### Asset Management

https://webpack.js.org/guides/asset-management/

<details>
        <summary>Loading CSS</summary>

1. Run Command: `$ npm install --save-dev style-loader css-loader`

2. In `webpack.config.js`, in `rules` add the following:

```js
 const path = require('path');

 module.exports = {
   entry: './src/index.js',
   output: {
     filename: 'main.js',
     path: path.resolve(__dirname, 'dist'),
   },

  module: {

    rules: [

      {

        test: /\.css$/i,

        use: ['style-loader', 'css-loader'],

      },

    ],

  },
 };
```

> Any file that ends with .css will be served to the `style-loader` and then the `css-loader`

3. Add `/src/style.css`. And write inside css.

4. Inside `src/index.js` import the css file:

```js
import './style.css';
```

5. Run build `$ npm run build`

</details>


<details>
        <summary>Loading Images</summary>

1. In `webpack.config.js`, in `rules` add the following:


```js
 const path = require('path');

 module.exports = {
   entry: './src/index.js',
   output: {
     filename: 'main.js',
     path: path.resolve(__dirname, 'dist'),
   },
   module: {
     rules: [
      {

        test: /\.(png|svg|jpg|jpeg|gif)$/i,

        type: 'asset/resource',

      },
     ],
   },
 };
```


2. Add image in `src/`, so it will be for example `src/myIcon.png`

3. Import it in `src/index.js`

```js
import Icon from './myIcon.png';
```

4. Run `$ npm run build`

</details>

<details>
        <summary>Loading Fonts</summary>

1. In `webpack.config.js`, in `rules` add the following:


```js
 const path = require('path');

 module.exports = {
   entry: './src/index.js',
   output: {
     filename: 'main.js',
     path: path.resolve(__dirname, 'dist'),
   },
   module: {
     rules: [
      {
        test: /\.css$/i,
        use: ['style-loader', 'css-loader'],
      },
      {
        test: /\.(woff|woff2|eot|ttf|otf)$/i,
        type: 'asset/resource',
      },
     ],
   },
 };
```


2. Add fonts in `src/`, so it will be for example `src/my-font.woff`
```
|- /src
  |- my-font.woff
  |- my-font.woff2
  |- style.css
  |- index.js
```

3. Import it in `src/style.css`

```css
@font-face {
  font-family: 'MyFont';
  src: url('./my-font.woff2') format('woff2'),
      url('./my-font.woff') format('woff');
  font-weight: 600;
  font-style: normal;

}
.hello {
  color: red;
  font-family: 'MyFont';
}
```

4. Run `$ npm run build`

</details>

<details>
        <summary>Loading Data</summary>

Another useful asset that can be loaded is data, like JSON files, CSVs, TSVs, and XML. Support for JSON is actually built-in, similar to NodeJS, meaning `import Data from './data.json'` will work by default. To import CSVs, TSVs, and XML you could use the csv-loader and xml-loader. Let's handle loading all three:

1. Run `$ npm install --save-dev csv-loader xml-loader`

2. In `webpack.config.js`, in `rules` add the following:


```js
 const path = require('path');

 module.exports = {
   entry: './src/index.js',
   output: {
     filename: 'main.js',
     path: path.resolve(__dirname, 'dist'),
   },
   module: {
     rules: [
      {
        test: /\.(csv|tsv)$/i,
        use: ['csv-loader'],
      },
      {
        test: /\.xml$/i,
        use: ['xml-loader'],
      },
     ],
   },
 };
```


3. Add data in `src/`, so it will be for example `src/data.xml`
```
|- /src
  |- data.xml
  |- data.csv
  |- style.css
  |- index.js
```

src/data.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<note>
  <to>Mary</to>
  <from>John</from>
  <heading>Reminder</heading>
  <body>Call Cindy on Tuesday</body>
</note>
```
src/data.csv
```csv
to,from,heading,body
Mary,John,Reminder,Call Cindy on Tuesday
Zoe,Bill,Reminder,Buy orange juice
Autumn,Lindsey,Letter,I miss you
```

4. Import it in `src/index.js`

```js
import Data from './data.xml';
import Notes from './data.csv';

//

console.log(Data);
console.log(Notes);
```
> Only the default export of JSON modules can be used without warning.
```js
// No warning
import data from './data.json';

// Warning shown, this is not allowed by the spec.
import { foo } from './data.json';
```

5. Run `$ npm run build`

</details>


### Source Maps

https://webpack.js.org/guides/development/

A handy way to track down which source file (index.js, a.js, b.js) an error is coming from when you use webpack to bundle them together.

<details>
        <summary>How to use Source Maps</summary>

1. In `webpack.config.js` set `mode: 'devlopment'` and `devtool: 'inline-source-map'`

```js
module.exports = {
  mode: 'development',
  // ...
  devtool: 'inline-source-map',
  // ...
};
```

2. Run `$ npm run build`

3. Open the resulting `index.html` file in your browser. Look in your console where the error is displayed. An example of an error from a `fileWithError.js` should say (after clicking on the HTMLButtonElement):

```
Uncaught ReferenceError: consssssole is not defined
   at HTMLButtonElement.printMe (fileWithError.js:2)
```

From an error in `fileWithError.js`:
```js
export default function printMe() {
  consssssole.log('I get called from print.js!');
}
```

</details>


### Development/Production Mode

https://webpack.js.org/guides/production/

Instead of manually switching between modes in the configuration file as needed, we can use `webpack-merge`. This can be quite useful as a quick setup can allow us to have a dedicated npm script for development builds/dev server, and another specifically for our production build.

> You’ll notice the above tutorial does not have a `webpack.config.js` file. If you do use `webpack-merge`, make sure that any webpack commands you run (including in an npm script) follow the tutorial and use the `--config` option to specify which webpack configuration file to use. If you do not specify one, webpack will try to look for `webpack.config.js` and if it does not find one, it will not be able to bundle correctly!


## More on Webpack

https://webpack.js.org/guides/