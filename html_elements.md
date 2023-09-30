# HTML Elements

## Hierarchy

Use ```div``` (block element)

Inside text use ```span``` (inline element)

## Elements

<details>
        <summary>Headers</summary>
  
        
```html
<h1> header 1 </h1>
```

```html
<h2> header 2 </h2>
```

```html
<h6> header 6 </h6>
```

</details>

<details>
        <summary>Text Elements</summary>

```html
<p> paragraph </p>
```
```html
<blockquote> quotation </blockquote>
```

</details>

<details>
        <summary>Text Manipulation</summary>
  
```html
<strong> bold </strong>
```
```html
<em> italic </em>
```
```html
<sub> subscript </sub>
```
```html
<sup> supscript </sup>
```

</details>

<details>
<summary>Absolute Link</summary>

```html
<a href="https://www.somewebsite.com" target="_blank" rel="noopener noreferrer">external website</a>
```

- ```target = ``` 
    - ```"_blank"```: open in new tab
    - ```"_self"```: open in this tab

- ```rel = ``` 
    - This attribute is used to describe the relation between the current page and the linked document.
    - ```"noopener"```: prevents the opened link from gaining access to the webpage from which it was opened
    - ```"noreferrer"```: prevents the opened link from knowing which webpage or resource has a link (or ‘reference’) to it.

</details>

</details>

<details>
<summary>Relative Link</summary>

- Link to other .html pages
```html
<a href="./about.html">About .html page in my directory</a>
<a href="./pages/about.html">about.html page in the /pages directory </a>
```
- Link within page
```html
<a href="#id-of-element">Will move to the element with the matching id</a>
```
</details>


<details>
        <summary>Lists</summary>

```html
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>
```
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>

---
```html
<ol>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ol>
```
<ol>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ol>

</details>

<details>
        <summary>Button</summary>

```html
<button class="button-class">button</button>
```
</details>

<details>
<summary>Images</summary>

- Image from link
```html
<img src="https://www.somewebsite.com/image.png" alt="description">
```
- Image from repo
```html
<img src="./myimages/image1.png" alt="description">
```

</details>

<details>
<summary>SVGs</summary>

- How they look like:
```html
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100">
    <rect x=0 y=0 width=100 height=50 />
    <circle class="svg-circle" cx="50" cy="50" r="10"/>
</svg>
```
Work like the other HTML elements mentioned.


- ```xmlns``` - stands for “XML NameSpace”. This specifies what dialect of XML you’re using. In our case, that dialect is the SVG language spec. Without it, some browsers will not render your image or will render it incorrectly. If you’re interested in a full breakdown of what this attribute is and why it’s necessary.
- ```viewBox``` - defines the bounds of your SVG. When you have to define the positions of different points of the elements in your SVG, this is what that’s referencing. It also defines the aspect ratio and the origin of your SVG. So it’s doing quite a lot! Be sure to play around with different values in the example above to get a feel for how it affects the shapes.
- ```class```, ```id``` - these attributes function just like they do in HTML. Using these in SVGs allows you to easily target an element via CSS or JavaScript, or to reuse an element via the ```use``` element.
```html
<svg viewBox="0 0 30 10" xmlns="http://www.w3.org/2000/svg">
  <circle id="myCircle" cx="5" cy="5" r="4" stroke="blue" />
  <use href="#myCircle" x="10" fill="blue" />
  <use href="#myCircle" x="20" fill="white" stroke="red" />
</svg>
```
- Elements such as ```<circle>```, ```<rect>```, ```<path>```, and ```<text>``` are defined by the SVG namespace. These are our basic building-blocks. Although you can make extremely complex images with SVG, they are mostly created with just a dozen or so of these basic elements. You can see a complete list of SVG elements here: https://developer.mozilla.org/en-US/docs/Web/SVG/Element
- Many SVG attributes, such as ```fill``` and ```stroke```, can be changed in your CSS. https://css-tricks.com/svg-properties-and-css/

### Resources
https://fonts.google.com/icons
https://feathericons.com/
https://thenounproject.com/term/free/
https://ionic.io/ionicons

</details>

<details>
<summary>Tables</summary>

```html
<table>
  <tr>
    <th>First Header</th>
    <th>Second Header</th>
  </tr>
  <tr>
    <td>This is a data cell</td>
    <td>This is also a data cell!</td>
  </tr>
</table>
```
<table>
  <tr>
    <th>First Header</th>
    <th>Second Header</th>
  </tr>
  <tr>
    <td>This is a data cell</td>
    <td>This is also a data cell!</td>
  </tr>
</table>

</details>
---

