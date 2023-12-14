# CSS Shape Properties

## Sizes
#### vh / vw
```css
width: 30vw;
height: 8vh;
```
#### px
```css
width: 100px;
height: 40px;
```
#### %
```css
width: 90%;
height: 90%;
```

## Box Model

```css
#demo-box-model {
  text-align: center;
  width: 40vw;

  /* Padding */
  padding: 10px 20px;

  /* Border */
  border-style: dotted;
  border-bottom-style: dashed;
  border-color: var(--dark);
  border-radius: 5px;

  /* Margin */
  margin: 20px;

  /* Outline */
  outline-style: dashed;
  outline-color: var(--dark);
  outline-offset: 20px;
}
```
Object -> Padding -> Border -> Margin -> Outline

<details>
    <summary>More: Shorthand</summary>

```css
margin: <margin-top> || <margin-right> || <margin-bottom> || <margin-left>
```

```css
outline: 2px dotted var(--dark-blue);
```
</details>

## Display

```css
display: inline;            /* start at next line */
```
```css
display: block;             /* start at on same line */
```
```css
display: inline-block;      /* like inline, but with margins/padding like block */
```

## Border Box
Margins and paddings add to the dimensions of a shape. These make the shape bigger, so orignal width/height aren't true. With 'border-box' it adjusts the size so that the original width/height (space taken by element) stays true. 
```css
box-sizing: border-box;
```

## Visibility
```css
opacity: 0.8; /* Between 0 and 1 */
```

> ❗ Give each individual item in that **hidden content** a **tabindex value of -1**

## Shadow

```css
box-shadow: 10px 10px 5px chocolate;
```

## Border

```css
h1 {
  border: 4mm ridge rgba(211, 220, 50, .6);
  border-radius: 50% 20% / 10% 40%;
}
```

## Overflow

```css
h1 {
  overflow: visible; /* hidden | clip | scroll | auto */
}
```

## Opacity

```css
h1 {
  opacity: 0.33;
}
```