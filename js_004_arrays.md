# JS Arrays

## Create Array
```js
let person1 = [];
let cars = ["Saab", "Volvo", "BMW"];
let cars2 = new Array("Saab", "Volvo", "BMW");
let points = new Array(40); // [ , , , , ,..., ] 40 empty spaces

// Assign Array Value
let name1 = cars[0];
```

## Array Methods
```js
// Length
let myArrayLength=cars.length;

// METHODS
// Sort
let myArraySorted = cars.sort(); 
// Type Of
let isArray = Array.isArray(cars);
// String
let to_string = cars.toString();
let seperater_string = cars.join(" * ");
```

## Modify
```js
// Add Modify Remove Return
delete cars[1]; // Remove at Index
cars[1]="Ferrari"; // Modify
let add_last = cars.push("Jaguar"); // Add to Last
let rem_ret_last = cars.pop(); // Remove Last
let add_first = cars.unshift("Mercedes"); // Add to First
let rem_ret_first = cars.shift(); // Rem/Ret First
let new_push_array = cars.concat("Volkswagen") // Adds to end (no modify)


// Replace (modifies)
let del_items=cars.splice(2, 0, "Honda", "Suzuki"); //index,remove,enter items


// Replace/Remove (non-mutating)
const some_array = ['a', 'b', 'c', 'd', 'e'];
const another_array = some_array.filter(a => a !== 'e');// ['a', 'b', 'c', 'd']
// OR
const another_array2 = some_array.filter(a => {
  return a !== 'e';
}); // ['a', 'b', 'c', 'd']
```

## Merging
```js
// Merging (no modificication -> const)
const cars3=["Citroen","Lexus"];
const cars4=["Nissan"];
const merge = cars.concat(cars3,cars4,"Land Rover"); 
const mergeBetter = [...cars3,...cars4,"Land Rover"]

// Slice
let slice = cars.slice(1, 3);

// Join
let array1 = [32,false,"js",12,56,90];
array1.join(";"); // = "32;false;js;12;56;90"
```

## Iterate
```js
let myPets = "";
let pets = ["cat", "dog", "hamster", "hedgehog"];
for (let pet of pets){
    myPets += pet + " ";
} // myPets = 'cat dog hamster hedgehog '
```

## Copy
```js
const items2 =["a","b","c"];
const itemsCopy = [...items2];
```

## Nodelist -> Array
```js
const fooNode = document.querySelectorAll('.foo');
// good
const arrayNodesBad = Array.from(fooNode);
// best
const arrayNodesGood = [...fooNode];
```

## Like Array -> Array
```js
const arrLike = { 0: 'foo', 1: 'bar', 2: 'baz', length: 3 };
const arrMadeBad = Array.prototype.slice.call(arrLike);// bad
const arrMadeGood = Array.from(arrLike);// good
```

## Map
```js
const fooMap = [1,2,3,4,5]
const barMap = (x) => x+1; 
const mapArrayBad = [...fooMap].map(barMap);// bad
const mapArrayGood = Array.from(fooMap, barMap);// good
```

## Destructuring
```js
const arrDestruct = [1, 2, 3, 4];
// bad
const firstDest = arrDestruct[0];
const secondDest = arrDestruct[1];
// good
const [firstDestGood, secondDestGood] = arrDestruct;
```

## Transform Data with Map
```js
const origArr = ['a', 'b', 'c', 'd', 'e'];
const transformedArr = origArr.map(n => n + 'Hi!'); // ['aHi!', 'bHi!', 'cHi!', 'dHi!', 'eHi!']
console.log(origArr); // ['a', 'b', 'c', 'd', 'e']; // orignal array is intact
```