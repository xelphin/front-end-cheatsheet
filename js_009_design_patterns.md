# JS Design Patterns

Good Source: https://www.patterns.dev/#patterns

## Object Constructors

```js
function Player(name, marker) {
  this.name = name;
  this.marker = marker;
  this.sayName = function() {
    return "My name is " + name;
  }
}

const myPlayer = new Player('Alice', 'X');

console.log(myPlayer.sayName); // 'My name is Alice'
```

## Factory Functions

```js
function createUser (name) {
  const discordName = "@" + name;

  let reputation = 0;
  const getReputation = () => reputation;
  const giveReputation = () => reputation++;

  return { name, discordName, getReputation, giveReputation };
}

const josh = createUser("josh");
josh.giveReputation();
josh.giveReputation();

console.log({
  discordName: josh.discordName,
  reputation: josh.getReputation()
});
// logs { discordName: "@josh", reputation: 2 }
```

Instead of `User(name)` (object constructor) it's `createUser(name)`.
<details>
<summary>Constructor version</summary>

```js
const User = function (name) {
  this.name = name;
  this.discordName = "@" + name;
}
```
</details>

<details>
<summary>About Closure</summary>

```js
  const counterCreator = () => {
    let count = 0;
    return () => {
      console.log(count);
      count++;
    };
  };
  
  const counter = counterCreator();
  
  counter(); // 0
  counter(); // 1
  counter(); // 2
  counter(); // 3
```
</details>



### Inheritance

```js
function createPlayer (name, level) {
  const { discordName, getReputation } = createUser(name);

  const increaseLevel = () => level++;
  return { name, discordName, getReputation, increaseLevel };
}

// or

function createPlayer (name, level) {
  const user = createUser(name);

  const increaseLevel = () => level++;
  return Object.assign({}, user, { increaseLevel });
}
```

## Module Pattern

```js
const calculator = (function () {
  const add = (a, b) => a + b;
  const sub = (a, b) => a - b;
  const mul = (a, b) => a * b;
  const div = (a, b) => a / b;
  return { add, sub, mul, div };
})();

calculator.add(3,5); // 8
calculator.sub(6,2); // 4
calculator.mul(14,5534); // 77476
```

In this example, we have a factory function creating some basic operations that we need only once. We can wrap it in parentheses and immediately call it by adding `()` - returning the result object that we store in `calculator`. In this way we can write code, **wrapping away things that we do not need as private variables and functions** inside our factory function and while they are tucked inside of our module, we can use the returned variables and functions outside the factory, as necessary.

#### Another Good Example

```js
const Formatter = (function() {
  let timesRun = 0;

  const log = (message) => console.log(`[${Date.now()}] Logger: ${message}`);
  const setTimesRun = () => { 
    log("Setting times run");
    ++timesRun;
  }

  const makeUppercase = (text) => {
    log("Making uppercase");
    setTimesRun();
    return text.toUpperCase();
  };

  const getTimesRun = () => {
    return timesRun;
  }

  return {
    makeUppercase,
    getTimesRun,
  }
})();


console.log(Formatter.makeUppercase("tomek"));
console.log(Formatter.getTimesRun());
```