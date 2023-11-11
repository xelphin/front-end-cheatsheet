# JS Object Functions

<details>
        <summary>source</summary>
  
From Wes Bos

JavaScript Array Cardio Practice - Day 1 — #JavaScript30​ 4/30 

</details>

We're going to use an example to demonstrate different object functions.

## Example

<details>
        <summary>inventors</summary>
  
```js
const inventors = [
  { first: 'Albert', last: 'Einstein', year: 1879, passed: 1955 },
  { first: 'Isaac', last: 'Newton', year: 1643, passed: 1727 },
  { first: 'Galileo', last: 'Galilei', year: 1564, passed: 1642 },
  { first: 'Marie', last: 'Curie', year: 1867, passed: 1934 },
  { first: 'Johannes', last: 'Kepler', year: 1571, passed: 1630 },
  { first: 'Nicolaus', last: 'Copernicus', year: 1473, passed: 1543 },
  { first: 'Max', last: 'Planck', year: 1858, passed: 1947 },
  { first: 'Katherine', last: 'Blodgett', year: 1898, passed: 1979 },
  { first: 'Ada', last: 'Lovelace', year: 1815, passed: 1852 },
  { first: 'Sarah E.', last: 'Goode', year: 1855, passed: 1905 },
  { first: 'Lise', last: 'Meitner', year: 1878, passed: 1968 },
  { first: 'Hanna', last: 'Hammarström', year: 1829, passed: 1909 }
];
```

</details>

<details>
        <summary>people</summary>
  
```js
const people = [
  'Bernhard, Sandra', 'Bethea, Erin', 'Becker, Carl', 'Bentsen, Lloyd', 'Beckett, Samuel', 'Blake, William', 'Berger, Ric', 'Beddoes, Mick', 'Beethoven, Ludwig',
  'Belloc, Hilaire', 'Begin, Menachem', 'Bellow, Saul', 'Benchley, Robert', 'Blair, Robert', 'Benenson, Peter', 'Benjamin, Walter', 'Berlin, Irving',
  'Benn, Tony', 'Benson, Leana', 'Bent, Silas', 'Berle, Milton', 'Berry, Halle', 'Biko, Steve', 'Beck, Glenn', 'Bergman, Ingmar', 'Black, Elk', 'Berio, Luciano',
  'Berne, Eric', 'Berra, Yogi', 'Berry, Wendell', 'Bevan, Aneurin', 'Ben-Gurion, David', 'Bevel, Ken', 'Biden, Joseph', 'Bennington, Chester', 'Bierce, Ambrose',
  'Billings, Josh', 'Birrell, Augustine', 'Blair, Tony', 'Beecher, Henry', 'Biondo, Frank'
];
```

</details>

<details>
        <summary>people2</summary>
  
```js
const people2 = [
  { name: 'Wes', year: 1988 },
  { name: 'Kait', year: 1986 },
  { name: 'Irv', year: 1970 },
  { name: 'Lux', year: 2015 }
];
```

</details>

<details>
        <summary>comments</summary>
  
```js
const comments = [
  { text: 'Love this!', id: 523423 },
  { text: 'Super good', id: 823423 },
  { text: 'You are the best', id: 2039842 },
  { text: 'Ramen is my fav food ever', id: 123523 },
  { text: 'Nice Nice Nice!', id: 542328 }
];
```

</details>


## Filter

Filter the list of inventors for those who were born in the 1500's

```js
const fifteen = inventors.filter(inventor => {
  if (inventor.year>=1500 && inventor.year<1600){
    return true; 
  }
}) 
```

## Map

Give us an array of the inventors first and last names

```js
const fullName = inventors.map(inventor => `${inventor.first} ${inventor.last}`);
console.log(fullName);
```

## Sort

<details>
        <summary>source</summary>
  
https://flaviocopes.com/how-to-sort-array-of-objects-by-property-javascript/

</details>

Sort the inventors by birthdate, oldest to youngest

```js
const ordered = inventors.sort(function(firstPerson,secondPerson){
  if (firstPerson.year > secondPerson.year){
    return 1 //secondPerson before firstPerson
  }
  else {
    return -1 //firstPerson before secondPerson
  }
  //1:sends b to be first // 2:sends a to be first
});

const ordered = inventors.sort((a,b)=> a.year>b.year ? 1:-1);
console.log(ordered);
```

## Reduce

```js
// How many years did all the inventors live all together?
const totalYears = inventors.reduce((total,inventor)=>{
  return total+ (inventor.passed-inventor.year)
},0); //total at start = 0

console.log(totalYears);
```

## Some

```js
const now = new Date();
const currentYear = now.getFullYear();
const isAdult = people2.some((person)=>(currentYear - person.year > 18));

console.log(isAdult);
```

## Every

```js
const now = new Date();
const currentYear = now.getFullYear();
const allAdults = people2.every((person) => (currentYear - person.year > 18));

console.log(allAdults);
```

## Find

Find is like filter, but instead returns just the one you are looking for.
Find the comment with the ID of 823423.

```js
const myID = comments.find(comment => comment.id===823423);
console.log(myID);
```

## Find Index

Find the comment with this ID.
Delete the comment with the ID of 823423
```js
const index = comments.findIndex(comment =>comment.id === 823423); //returns 1 (index)
comments.splice(index,1);
console.log(comments);
```
