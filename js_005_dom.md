# JS DOM


## Targeting nodes with selectors

```html
<div id="container">
  <div class="display"></div>
  <div class="controls"></div>
</div>
```
```js
const container = document.querySelector('#container');
// select the #container div
console.dir(container.firstElementChild);
// select the first child of #container => .display
const controls = document.querySelector('.controls');   
// select the .controls div
console.dir(controls.previousElementSibling);
// selects the prior sibling => .display
let images = document.body.getElementsByTagName("img");
// nodelist of all images in document body
```

## Query selector nodelist

```js
element.querySelector('.controls') // --returns reference to first match
element.querySelectorAll('.controls') // --reference to all (nodelist)
```
> this doesn't return an 'array'! It returns a 'nodelist'.
> can use Array.from() or spread operator to use some array methods
```js
const divChildren2 = document.querySelectorAll('.head-div-child');
const headDiv = document.querySelector('#head-div');
let divChildren = headDiv.childNodes;
let divChildrenArray = Array.from(divChildren);
//
let myPs = document.querySelectorAll("p");
let amountOfPs = myPs.length;
let secP= myPs[1];
for (let i = 0; i < myCollection.length; i++) {
  myPs[i].style.color = "gray";
}
```

## Create Element
`document.createElement(tagName, [options])` creates a new element of tag type `tagName`. `[options]` in this case means you can add some optional parameters to the function.
```js
//document.createElement(tagName[, options])
const myDiv = document.createElement('div'); //not yet inside DOM
```
This function does NOT put your new element into the DOM - it simply creates it in memory. This is so that you can manipulate the element (by adding styles, classes, ids, text, etc.) before placing it on the page. You can place the element into the DOM with one of the following methods.

## Append Element
appends childNode as the last child of parentNode

```js
parentNode.appendChild(childNode);
```
inserts childNode in parentNode before referenceNode

```js
parentNode.insertBefore(newNode, referenceNode);
```

## Remove Elements
```js
const expendable = document.querySelector('#expendable');
//parentNode.removeChild(child)
container.removeChild(expendable);
//  ^removes child from parentNode
```

## Replace Elements
```js
let newImage=images[0];
let newText=document.createTextNode("text replaced image alt");
newImage.parentNode.replaceChild(newText, newImage); //image is replaced by text
```

## Adding Inline Styles
```js
myDiv.style.color = 'blue';                             
//  ^adds the indicated style rule
myDiv.style.cssText = 'color: blue; background: white'; 
//  ^adds several style rules
myDiv.setAttribute('style', 'color: blue; background-color: white; font-size:15px;');    
//  ^adds several style rules
//Apply CSS using id/class (take a look at css code)
myDiv.setAttribute('id','bar');
myDiv.classList.add('foo');
```

### Good Example
```js
var divStyle = document.querySelector('div').style;

//set
divStyle.backgroundColor = 'red';
divStyle.border = '1px solid black';
divStyle.width = '100px';
divStyle.height = '100px';

//get
console.log(divStyle.backgroundColor);
console.log(divStyle.border);
console.log(divStyle.width);
console.log(divStyle.height);
```

## Removing Inline Styles
```js
myDiv.style.color= '';
myDiv.style.removeProperty('font-size');
//Note! when doing myDiv.style.property, property is camelCase and doesn't have hyphens.
console.log("myDiv background: "+window.getComputedStyle(myDiv).background);

```

## Getting Inline Styles
```js
let theWidth=myDiv.style.width; //can only get it if it's written in the html
```

## Editing Attributes
```js
myDiv.setAttribute('id', 'theDiv');                     
// if id exists update it to 'theDiv' else create an id
// with value "theDiv"
myDiv.getAttribute('id');                               
// returns value of specified attribute, in this case
// "theDiv"
myDiv.removeAttribute('id');                            
// removes specified attribute
```

## Working with Classes
```js
myDiv.classList.add('new');
// adds class "new" to your new div
myDiv.classList.remove('new');  
// remove "new" class from div
myDiv.classList.toggle('active'); 
// if div doesn't have class "active" then add it, or if
// it does, then remove it
```

## Adding Text Context
```js
myDiv.textContent = 'Hello World!'
// creates a text node containing "Hello World!" and
// inserts it in div
```

## Quick: Adding Element to Webpage
```js
const someDiv = document.querySelector('#container2');

const content = document.createElement('div');
content.classList.add('content'); //class:"content"
content.textContent = 'This is the glorious text-content!';

someDiv.appendChild(content);
```