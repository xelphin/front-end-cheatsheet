# JS Objects

## Init
```js
let someVariable ="apple"
let object0 = new Object(); 
const object1 = {
  a: 'somestring',
  b: 42,
  c: false,
  d: 32,
  e: "otherstring"
};
let object2={
  name:"John",
  age:22,
  "likes birds":true,
  [someVariable]:2
}
```

## Access Entries
```js
Object.keys(object1); //[a,b,c]
Object.values(object1) //["somestring", 42, false]
object2.age; //22
object2["likes birds"]; //true 
```

## Iterate over Entries
```js
for (const [key, value] of Object.entries(object1)) {
  console.log(`${key}: ${value}`);
}
for (let key in object2) {
  console.log( key );  // name, age, isAdmin
  console.log( object2[key] ); // John, 22, true
}
console.log("likes birds?",object2["likes birds"]) //true
console.log("name:",object2.name) //John
```

## Key Existance
```js
let user = { name: "John", age: 30 };
let ageExists = ("age" in user); // true

```

## Change Entries
```js
//Change Entry
object2["likes birds"] = true;

//Add Entry
object2.isAdmin = true;
object2["car"]="Mercedes"

//Delete Entry
delete object2.age;

```

## Property value shorthand
```js
function makeUser(name, age) {
  return {
    name: name,
    age: age,
    // ...other properties
  };
}

let user = makeUser("John", 30);

// Can become this ->

function makeUser(name, age) {
  return {
    name, // same as name: name
    age,  // same as age: age
    // ...
  };
}

```

## List to Object
```js
//Make an Object from list of key:value pairs
const entries = new Map([
  ['foo', 'bar'],
  ['baz', 42]
]);
const obj = Object.fromEntries(entries);
console.log(obj);// Object { foo: "bar", baz: 42 }

```

## Undefined
```js
//Undefined
console.log( object2.interest === undefined)// true,
//console.log( age in object2 ); //false (deleted)

```

## Delete
```js
//Splice
object1.splice(3,1) //delete (key:value) at index 3

```

## Copy Object
```js
/* COPY */
const original = { a: 1, b: 2 };
const copy = { ...original, c: 3 }; // copy => { a: 1, b: 2, c: 3 }

const { a, ...theRest } = copy; // theRest => { b: 2, c: 3 }
```

## Call Functions Through Objects

### Method 1
```js
function add (a,b) {
    return a+b;
}
// ...

const evaluateOperation = {
    "+": add,
    "-": subtract,
    "*": multiply,
    "/": divide
}
```

And then you call it like so:

```js
evaluateOperation["+"](12, 4);
```

### Method 2
In case you want to control arguments

```js
function setOperation(symbol) {
    // ...
}

const addSymbol = {
    "+": function() { setOperation("+"); }
    // ...
};
```
And then you call it like so:

```js
addSymbol["+"]();
```