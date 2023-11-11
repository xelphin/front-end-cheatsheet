# JS Prototype

<details>
<summary>Background</summary>

```js
Object.getPrototypeOf(player1) === Player.prototype // returns true
Object.getPrototypeOf(player2) === Player.prototype // returns true
```
Any properties or methods defined on ```Player.prototype``` will be available to the **created Player objects**.

```js
Player.prototype.sayHello = function() {
   console.log("Hello, I'm a player!");
}

player1.sayHello() // logs "Hello, I'm a player!"
player2.sayHello() // logs "Hello, I'm a player!"
```
Here, we defined the ```.sayHello``` function ‘on’ the ```Player.prototype``` object. It then became available for the ```player1``` and the ```player2``` objects to use! Similarly, you can attach other properties or functions you want to use on all ```Player``` objects by defining them on the objects’ prototype (```Player.prototype```).

Every prototype object inherits from ```Object.prototype``` by default. (Has functions like ```valueOf()``` which I can call like so: ```player1.valueOf()```)

</details>

## Another Example

```js
// Initialize constructor functions
function Hero(name, level) {
  this.name = name;
  this.level = level;
}

function Warrior(name, level, weapon) {
  Hero.call(this, name, level);

  this.weapon = weapon;
}

function Healer(name, level, spell) {
  Hero.call(this, name, level);

  this.spell = spell;
}

// Link prototypes and add prototype methods
Object.setPrototypeOf(Warrior.prototype, Hero.prototype);
Object.setPrototypeOf(Healer.prototype, Hero.prototype);

Hero.prototype.greet = function () {
  return `${this.name} says hello.`;
}

Warrior.prototype.attack = function () {
  return `${this.name} attacks with the ${this.weapon}.`;
}

Healer.prototype.heal = function () {
  return `${this.name} casts ${this.spell}.`;
}

// Initialize individual character instances
const hero1 = new Warrior('Bjorn', 1, 'axe');
const hero2 = new Healer('Kanin', 1, 'cure');
```

<details>
<summary>From</summary>

https://www.digitalocean.com/community/tutorials/understanding-prototypes-and-inheritance-in-javascript

</details>

> Using setPrototypeOf() `after` objects have already been created can result in `performance issues`.
