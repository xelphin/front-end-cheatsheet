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

---