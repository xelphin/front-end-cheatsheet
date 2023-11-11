# CSS Selectors

## Selectors

### Universal
```css
* {
  color: purple;
}
```

### Type
```css
div {
  color: white;
}
```

### Class
```css
.read {
  font-size:0.5em;
}
```

## Combination Selectors

### Shared
```css
.class1,
.class2 {
  color: white;
  background-color: black;
}

.class1 {
  font-size:0.5em;
}
```

### Multiple Attributes
```css
.class1.class2 {
  color: red;
}

.class1#id1 {
  color: blue;
}
```

## Relation Selectors

#### html
```html
<main class="parent">
  <div class="child group1">
    <div class="grand-child group1"></div>
  </div>
  <div class="child group2">
    <div class="grand-child group2"></div>
  </div>
  <div class="child group3">
    <div class="grand-child group3"></div>
  </div>
</main>
```
#### css


<details>
        <summary>Children</summary>

```css
main div {
  /* all children and grandchildren */
}
```
```css
main > div {
  /* all children */
}
```
```css
main > div > div{
  /* all grandchildren */
}
```
</details>

<details>
        <summary>Siblings</summary>

```css
.group1 + div {
  /* only div with the class "child group2" */
}
```
```css
.group1 + div + div {
  /* only div with the class "child group3" */
}
```
```css
.group1 ~ div {
  /* select all of .group1's siblings - in this case the 2nd and 3rd .child divs */
}
```
</details>


### Backwards ancestry
```css
.child-class > .ancestor-class {
  color: red;
}
```

## Dynamic and user action pseudo-classes

Example
```css
/* This will apply to unvisited links */
a:link {
  color: blue;
}

/* And you guessed it, this applies to all links the user has clicked on */
a:visited {
  color: purple;
}
```
Other:

- ```:focus``` element currently selected by user
- ```:hover``` element who has user mouse over it
- ```:active``` element that is being clicked

## Structural pseudo-classes
 
<details>
        <summary>:root</summary>

represents the very top level of your document - the one element that has no parents. Generally when working with the web, this is equivalent to the html element

is generally the place where you will place your ‘global’ CSS rules that you want available everywhere - such as your custom properties and CSS variables, or rules such as box-sizing: border-box;

</details>

<details>
        <summary>:first-child and :last-child </summary>

will match elements that are the first or last sibling

</details>

<details>
        <summary>:empty </summary>

match elements that have no children at all

</details>

<details>
        <summary>:only-child </summary>

will match elements that don’t have any siblings

</details>

<details>
        <summary>:nth-child </summary>

```css
.myList:nth-child(5) {/* Selects the 5th element with class myList */}

.myList:nth-child(3n) { /* Selects every 3rd element with class myList */}

.myList:nth-child(3n + 3) { /* Selects every 3rd element with class myList, beginning with the 3rd */}

.myList:nth-child(even) {/* Selects every even element with class myList */}
```

</details>

## Pseudo-Elements

<details>
        <summary>::marker</summary>

allows you to customize the styling of your <li> elements’ bullets or numbers.

</details>
<details>
        <summary>::first-letter and ::first-line</summary>

allows you to give special styling to the first letter or line of some text

</details>
<details>
        <summary>::selection</summary>

allows you to change the highlighting when a user selects text on the page.

</details>
<details>
        <summary>::before and ::after</summary>

allow us to add extra elements onto the page with CSS, instead of HTML. Using it to decorate text in various ways is one common use case.

```html
<style>
  .emojify::before {
    content: '😎 🤓';
}

  .emojify::after {
    content: '🤓 😎';
}
</style>

<body>
  <div> Let's <span class="emojify">emojify</span>this span!</div>
</body>
```
We'll get: ```Let’s 😎 🤓 emojify 🤓 😎 this span!```

</details>

## Attribute Selectors

Attribute is simply anything in the opening tag of an HTML element - such as ```src='picture.jpg'``` or ```href="www.theodinproject.com"```



- ```[attribute]``` - This general selector will select anything where the given attribute exists. Its value doesn’t matter.
- ```selector[attribute]``` - Optionally we can combine our attribute selectors with other types of selectors, such as class or element selectors.
- ```[attribute="value"]``` - To get really specific, we can use = to match a specific attribute with a specific value.

<details>
        <summary>Demo</summary>

```css
[src] {
  /* This will target any element that has a src attribute. */
}

img[src] {
  /* This will only target img elements that have a src attribute. */
}

img[src="puppy.jpg"] {
  /* This will target img elements with a src attribute that is exactly "puppy.jpg" */
}
```
</details>




- ```[attribute^="value"]``` - ```^=``` Will match strings from the start.
- ```[attribute$="value"]``` - ```$=``` Will match strings from the end.
- ```[attribute*="value"]``` - ```*=``` The wildcard selector will match anywhere inside the string.



<details>
        <summary>Demo</summary>
        
```css
[class^='aus'] {
  /* Classes are attributes too!
    This will target any class that begins with 'aus':
    class='austria'
    class='australia'
  */
}

[src$='.jpg'] {
  /* This will target any src attribute that ends in '.jpg':
  src='puppy.jpg'
  src='kitten.jpg'
  */
}

[for*='ill'] {
  /* This will target any for attribute that has 'ill' anywhere inside it:
  for="bill"
  for="jill"
  for="silly"
  for="ill"
  */
}
```
</details>
