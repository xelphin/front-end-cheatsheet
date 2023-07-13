# JS Basic

## Add to HTML

```html
<script src="javascript.js" defer></script>
```
Add this inside of the `body` tag, at the bottom.

## Comments

```js
//One Line Comment
/*
*Multiple Lines
*Multiple Lines
*/
//FIXME: Here a note on what to fix
//TODO: Here a note on task still needed to implement
```

## Variables
```js
let message; //message=undefined
isNaN(message); // checks if NaN (not a number)
message="hello";
const COLOR_RED = "#F00";
let s1= ("5"==5) //true
let s2= ("5"===5) //false
s1= (null==undefined) //true
s2= (null===undefined) //false
let s3=5;
s3+=6; //s3=11
s3*=2; //s3=22
typeof s3; // number
```



## Numbers

```js
let num1=123e-5;
num1 = 0xFF;// x will be 255 (hexadecimal)
string1=num1.toString(10); //toString(base 10) 
//String to Number
let num31="22";
num31=Number(num31); //if not number then NaN
//String Object
let num2 = new Number(123); //object type Number
//objects can't be compared so num2==num3 will always be false
//Round
num1 = num1.toFixed(2); //rounds it to two decimal places
//typeof num1;
num1=Math.round(3.4542 * 10) / 10; //2.0->to just 2 though
typeof 10n // "bigint"

```

## Accuracy

```js
let xAcc = 0.2 + 0.1; // == 0.30000000000000004
let xMoreAcc = (0.2 * 10 + 0.1 * 10) / 10; // == 0.3
```

## MATH

```js
Math.min(42, 6, 27); // = 6
Math.min([42, 6, 27]); // = NaN (uh-oh!)
Math.min.apply(Math, [42, 6, 27]); // = 6
```

## String

```js
let phrase1="string"
let phrase2 = `can embed another ${phrase1}`;
phrase2 = 'I\'ve got no right to take my place...';
let joined1 = phrase1 + phrase2 + 3 + " and so on...";
//Length
let num3= phrase1.length; //6
//To String
phrase1 = num3.toString(); //"6"
//Find Index
let phrase3 = "Please locate where 'locate' occurs!";
let index1 = phrase3.indexOf("locate");
let index2 = phrase3.lastIndexOf("locate");//can't take powerful search values
let index3 = phrase3.search("locate"); //can't take a start position value
//Find Char at Index
let char1 = "This is a string".charAt(0); 
//Extract String Parts
phrase2 = "Apple, Banana, Kiwi";
console.log("split: ",phrase2.split(", "));
console.log("split-find[2]: ",phrase2.split(", ")[2]);
phrase3 = phrase2.slice(7, 13);//Banana (also: (-12, -6))
phrase3 = phrase2.slice(7);//Banana, Kiwi
phrase3 = phrase2.substr(7, 6);//Banana (length=6)
phrase2=phrase2.replace("Apple", "Mango");
phrase2= phrase2.replace(/BANanA/i, "Papaya");//case insensitive
phrase2=phrase2.replace(/Kiwi/g, "Pineapple");//replace all
//uppercase/lowercase
phrase2=phrase2.toUpperCase(); 
phrase2=phrase2.toLowerCase(); 
//trim
phrase2 = "       Hello World!        ";
phrase2=phrase2.trim();
//char at
phrase3=phrase2.charAt(0);
phrase3=phrase2[0];
phrase3[0] = "A";
//replace
phrase3="asd dfg asd"; 
phrase3=phrase3.split("d").join(""); //as fg as
phrase3=phrase3.replace(" ",""); //asfg as
console.log(phrase3);
//string to array
phrase3 = "a,b,c,d,e";
phrase3=phrase3.split(","); 
//delete all non alphabet character
phrase3 = "abc??de$$fg";
phrase3= phrase3.replace(/\W/g, ''); //abcdefg

```

## If
```js
let time=4;
if (time < 10) {
  greeting = "Good morning";
} else if (time < 20) {
  greeting = "Good day";
} else {
  greeting = "Good evening";
}
```

## Switch
```js
let day = 3
switch (day) {
    case 1:
        console.log("Start of the week!");
        break;
    case day>1 && day<5:
        console.log("Almost Friday");
        break;
    case 5:
        console.log("Happy Friday!");
        break;
    case 6:
    case 7:
        console.log("Weekend!");
        break;
    default:
        console.log("Not a correct day...");
}
```

## While

```js
console.log("While:")
let counter=0
while (counter<3){
    counter+=1;
}
console.log(counter);
```

## Do While
```js
let doResult = '';
let doI = 0;

do { //executes at least once
  doI = doI + 1;
  doResult = doResult + doI;
} while (doI < 5);
```

## For Loop

```js
let forResult=""
for (let forI = 0; forI < 3; forI++){
    forResult+="bam";
} //forResult = "bambambam"
//Break Loop
outer:
for (let forI =0; forI<5; forI++){
  if (forI==2){
    break outer;
  }
  forResult+="cha"
} //forResult = "bambambamchacha"
```


