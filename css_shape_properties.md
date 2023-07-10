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

