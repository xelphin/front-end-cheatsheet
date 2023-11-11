# JS Events


## Adding Event Listeners
```js
//Method 1
const myContainer = document.querySelector('#container3');
const btn1 = document.querySelector('#btn1');
btn1.onclick = () => alert("Hello World");

//Method 2 <3
const btn2 = document.querySelector('#btn2');
btn2.addEventListener('click', () => {
  alert("Hello World");
});

//Method 3
function alertFunction() { //in html: onclick="alertFunction()"
  alert("YAY! YOU DID IT!");
  event.target.getAttribute("id");
  //if set 'style', make sure it's already added in html to change
  event.currentTarget.getAttribute("id");
  //So when element.addEventListener(...)
  //It makes sure that the target is element and not one of its chidlren
}

//Method 4
const btn4 = document.querySelector('#btn4');
btn4.onclick = alertFunction;

//Method 5 <3
const btn5 = document.querySelector('#btn5');
btn5.addEventListener('click', alertFunction);
```

## Removing Event Listeners
```js
btn5.removeEventListener('click', alertFunction);
```

## Event Objects
```js
let btn7 = document.querySelector("#btn7");
btn7.addEventListener("click", event => {
  //event handler functions are passed an argument: the event object
  //this object holds additional information about the event.
  if (event.button == 0) {
    alert("Left button");
  } else if (event.button == 1) {
    alert("Middle button");
  } else if (event.button == 2) {
    alert("Right button");
  }
});
document.body.addEventListener("click", event => {
  if (event.target.nodeName == "BUTTON") {
    console.log("Clicked", event.target.textContent);
  }
});
```

## Adding event listeners with callbacks
```js
//example
const btn6 = document.querySelector("#btn6");
btn6.addEventListener('click', function(e) {
  alert(e); //-> [object MouseEvent]
  alert(e.target); //->[object HTMLButtonElement]
  e.target.style.background = 'white';
});
```

## Attaching listeners to groups of nodes
```js
// buttons is a node list. It looks and acts much like an array.
const buttons = document.querySelectorAll('button');
// we use the .forEach method to iterate through each button
// buttons is being sent to forEach() which gives a callback for each button
buttons.forEach((button) => {
  // and for each one we add a 'click' listener
  button.addEventListener('click', () => {
    alert(button.id);
  });
});
```

## Key events
```js
//when user pressed 'v' key, page turns black
window.addEventListener("keydown", event => {
  if (event.key == "v") {
    //remember this repeats itself as long as the key is pressed
    //so be careful
    document.body.style.background = "black";
  }
});
window.addEventListener("keyup", event => {
  if (event.key == "v") {
    document.body.style.background = "";
  }
});
```

## Pass arguments to event
```js
let mainTitle= document.createElement("div")
let dblTitle = (event) => editText(event,"hello","title");
mainTitle.addEventListener("dblclick", dblTitle);
//
function editText(event, text, type){
  event.currentTarget.textContent= text;
  console.log("Type: ",type);
}


/*---DRAWING PAD EXAMPLE---*/
const drawpad = document.querySelector(".drawpad");
drawpad.addEventListener("click", event => {
  let dot = document.createElement("div");
  dot.className = "dot";
  dot.style.left = (event.pageX - 4) + "px";
  dot.style.top = (event.pageY - 4) + "px";
  drawpad.appendChild(dot);
});



/*---MOUSEMOTION---*/
let lastX; // Tracks the last observed mouse X position
let bar = document.querySelector("#drag-bar");
bar.addEventListener("mousedown", event => {
  if (event.button == 0) {
    console.log(event);
    lastX = event.clientX;
    window.addEventListener("mousemove", moved);
    event.preventDefault(); // Prevent (Default) selection
  }
});
function moved(event) {
  if (event.buttons == 0) {
    window.removeEventListener("mousemove", moved);
  } else {
    let dist = event.clientX - lastX;
    let newWidth = Math.max(10, bar.offsetWidth + dist);
    bar.style.width = newWidth + "px";
    lastX = event.clientX;
  }
}


/*---SCROLL---*/
let progBar = document.querySelector("#progress");
window.addEventListener("scroll", () => {
  let max = document.body.scrollHeight - innerHeight;
  progBar.style.width = `${(pageYOffset / max) * 100}%`;
});


/*---FOCUS EVENTS---*/
let help = document.querySelector("#help");
let fields = document.querySelectorAll("input");
for (let field of Array.from(fields)) {
  field.addEventListener("focus", event => {
    let text = event.target.getAttribute("data-help");
    help.textContent = text;
  });
  field.addEventListener("blur", event => {
    help.textContent = "";
  });
}
```

## Debouncing
```js
//when multiple events happen at once, instead of having the page load slowly
//we can debounce: setTimeout
//makes sure you are not doing it too often
let textarea = document.querySelector("textarea");
let timeout;
textarea.addEventListener("input", () => {
  clearTimeout(timeout);
  timeout = setTimeout(() => console.log("Typed!"), 500);
});
//type quickly, the 'Type' message will show up later
```

## Other Useful Events other than click
-    click
-    dblclick
-    keypress
-    keydown
-    keyup

Full list:
https://www.w3schools.com/jsref/dom_obj_event.asp