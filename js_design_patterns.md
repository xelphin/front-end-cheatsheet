# JS Design Patterns

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
