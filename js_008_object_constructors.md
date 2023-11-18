# JS Object Constructors

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

## Classes

Like the above, but a bit different

```js
class User {

  #privateField = 5;

  constructor(name) {
    this.name = name*this.#privateField;
  }

  sayHi()  {
    alert(this.name);
  }

  // OR

  sayHi = () => {
    alert(this.name);
  }
  // For when you "lose this" (function binding)

}

// Usage:
let user = new User("John");
user.sayHi();
```

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes

## Extend

https://www.w3schools.com/jsref/jsref_class_extends.asp

```js
class Car {
  constructor(brand) {
    this.carname = brand;
  }
  present() {
    return 'I have a ' + this.carname;
  }
}

class Model extends Car {
  constructor(brand, mod) {
    super(brand);
    this.model = mod;
  }
  show() {
    return this.present() + ', it is a ' + this.model;
  }
}

mycar = new Model("Ford", "Mustang");
document.getElementById("demo").innerHTML = mycar.show();
```

https://javascript.info/class


## Static Property

```js
class ClassWithStaticMethod {
  static staticProperty = 'someValue';
  static staticMethod() {
    return 'static method has been called.';
  }
  static {
    console.log('Class static initialization block called');
  }
}

// Even though I didn't create an instance, I can call the fields/methods


console.log(ClassWithStaticMethod.staticProperty);
// Expected output: "someValue"
console.log(ClassWithStaticMethod.staticMethod());
// Expected output: "static method has been called."
```


## Named Class Expressions

```js
let User = class MyClass {
  sayHi() {
    alert(MyClass); // MyClass name is visible only inside the class
  }
};

new User().sayHi(); // works, shows MyClass definition

alert(MyClass); // error, MyClass name isn't visible outside of the class
```

## Dynamic Classes

```js
function makeClass(phrase) {
  // declare a class and return it
  return class {
    sayHi() {
      alert(phrase);
    }
  };
}

// Create a new class
let User = makeClass("Hello");

new User().sayHi(); // Hello
```


## Getters and Setters

https://javascript.info/property-accessors

```js
let user = {
  name: "John",
  surname: "Smith",

  get fullName() {
    return `${this.name} ${this.surname}`;
  },

  set fullName(value) {
    [this.name, this.surname] = value.split(" ");
  }
};

// set fullName is executed with the given value.
user.fullName = "Alice Cooper";

alert(user.name); // Alice
alert(user.surname); // Cooper


// As a Class:

class User {

  constructor(name) {
    // invokes the setter
    this.name = name;
  }

  get name() {
    return this._name;
  }

  set name(value) {
    if (value.length < 4) {
      alert("Name is too short.");
      return;
    }
    this._name = value;
  }

}

let user = new User("John");
alert(user.name); // John

user = new User(""); // Name is too short.
```

## Define Property

https://javascript.info/property-accessors

But sooner or later, things may change. Instead of age we may decide to store birthday, because it’s more precise and convenient:
Now what to do with the old code that still uses age property?
We can try to find all such places and fix them, but that takes time and can be hard to do if that code is used by many other people. And besides, age is a nice thing to have in user, right?
Let’s keep it.
```js
function User(name, birthday) {
  this.name = name;
  this.birthday = birthday;

  // age is calculated from the current date and birthday
  Object.defineProperty(this, "age", {
    get() {
      let todayYear = new Date().getFullYear();
      return todayYear - this.birthday.getFullYear();
    }
  });
}

let john = new User("John", new Date(1992, 6, 1));

alert( john.birthday ); // birthday is available
alert( john.age );      // ...as well as the age
```

## Computed Names

```js
class User {

  ['say' + 'Hi']() {
    alert("Hello");
  }

}

new User().sayHi();
```