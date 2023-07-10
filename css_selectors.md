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

### Descendant
```css
.ancestor-class .child-class {
  color: red;
}
```
<details>
<summary>Example</summary>

```html
<!-- index.html -->

<div class="ancestor">
  <!-- A -->
  <div class="contents">
    <!-- B -->
    <div class="contents"><!-- C --></div>
  </div>
</div>

<div class="contents"></div>
<!-- D -->
```
A and B will have the color red

</details>

### Descendant
```css
.child-class > .ancestor-class {
  color: red;
}
```