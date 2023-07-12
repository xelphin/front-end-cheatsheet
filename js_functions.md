# JS Functions


```js
/*---NORMAL FUNCTIONS---*/
function myFunction(thing){
    return thing.toUpperCase();
}
myFunction("foo"); // = "FOO"

```

## Anonymous Functions
```js
const myGreeting = function(person) {
  console.log('Hello '+person);
}
myGreeting("Alice");

```

## Named Function Expression
```js
const myGreeting2 = function uniqueGreet(person) {
  console.log('Hello '+person);
};
myGreeting2("Alice2");
```

## Arrow Functions
```js
let sum = (a, b) => a + b; //arguments=(a,b) return=a+b
const chocoFunction = (chocolate, isSad) => {
  if (isSad) 
    console.log('Eat: ' +  chocolate);
}
const playThe = funky => { //1 argument, () can be ommitted
  return funky + " music";
}
const playThat = () => "funky music";
```

## Callbacks
```js
const notes = ['do', 're', 'mi'];
notes.forEach((item) => console.log(item)); //each time sends back (callback) a different 'item'
```

## Iterator Functions (Callbacks)
```js
function myForEach(array, callback) {
  for (let i = 0; i < array.length -1; i++) {
    callback(array[i]); // This is when the callback function gets called, or executed
    //At each callback(), it returns to myForEach() a value
  }
}
// You would call it like this:
const myArry = [2, 3, 4, 2];
myForEach(myArry, (item) => {
  //'item' will always be a new value, for each callback() return we get
  console.log(item + 2); 
})
```

## CALL , APPLY , BIND
```js
console.log("apply, bind:")
let someObj = {
    myString: "Hello World!",
    myFunc: function(){
        return this.myString;
    }
};
let anotherFunc = function(s){
    return this.myString + s; //this.myString = "Hello World!"
};
console.log(anotherFunc.call(someObj, " And Hello Moon!"));
anotherFunc.apply(someObj, [" And Hello Sun!"]); // = "Hello World! And Hello Sun!"
let boundFunc = anotherFunc.bind(someObj);
boundFunc(" And Hello Saturn!"); // = "Hello World! And Hello Saturn!"
// //
let product = function(a, b){ return a * b; };
let doubler = product.bind(this, 2);
doubler(8); // = 16
// //
let MyConstructor = function(){
    this.myNumber = 5;
};
myNewObj = new MyConstructor(); // = {myNumber: 5}
myNewObj.myNumber; // = 5
// //
console.log("Function- someObj.hasOwnProperty(x):");
for (let x in someObj){
    if (someObj.hasOwnProperty(x)){
        console.log(someObj[x]);
    }
}
```

## Function Expression
```js
let age=20;
let welcome = (age < 18) ?
  function() { console.log("Hello!"); } :
  function() { console.log("Greetings!"); };
welcome(); //can only call after the function block
```

## Arguments
```js
//Use Argument
function favoriteAnimal(animal) {
  console.log(animal + " is my favorite animal!")
}
favoriteAnimal('Goat')

//Default Argument
function showMessage(from, text = "no text given") {
  alert( from + ": " + text );
}

//Unpassed Argument
function showMessage(from, text = anotherFunction()) {
  // anotherFunction() only executed if no text given
  // its result becomes the value of text
}

//If Argument is Empty
function showMessageBad(text) {
  //DON'T DO THIS!
  text = text || 'empty';
}
function showMessageBetter(text = "empty") {
  console.log(text);
}

//Nullish Operator
function showCount(count) {
  console.log(count ?? "unknown");
}
showCount(0); // 0
showCount(null); // unknown
showCount(); // unknown


//Multiple (unknow amount argument)
const makeArray = function() {
    let arr = Array.from(arguments); 
    return arr; 
}
console.log(makeArray([1,4,5],"hello",99,2,1));
//Preferred:
function concatenateAll(...args) { //don't call args 'arguments'
  return args.join('');
}


//Create Node, treat rest arguments as children
function elt(type, ...children) {
  let node = document.createElement(type);
  for (let child of children) {
    if (typeof child != "string") node.appendChild(child);
    else node.appendChild(document.createTextNode(child));
  }
  return node;
}

```

## Function as Argument
```js
function operate(operation,a,b){
  //operation is type string
    const functionNames = {
        "add":add(a,b),
        "subtract":subtract(a,b),
        "multiply":multiply(a,b),
        "divide":divide(a,b),
        "power":power(a,b),
        "modulo":modulo(a,b)
    }
    return functionNames[operation].toString();  
}

let myObj = {
    myFunc: function(){
        return "Hello world!";
    }
};
console.log(myObj.myFunc());
//myFunc(); // = undefined
```