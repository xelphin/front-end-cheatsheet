# CSS Responsiveness

### Viewport Meta Tag

To set the initial width of the webpage to the size of the actual screen you’re viewing it on, and telling it not to zoom in or out do:

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

## Media Queries

```css
/*  the margin will be 8px, and on all screens above 600px, it will be 24px */
body {
  margin: 24px;
}

/* all screens below or equal to 600px */
@media (max-width: 600px) {
  body {
    margin: 8px;
  }
}
```

### Multiple Media Queries

```css
body {
  background: purple;
}

@media (max-width: 800px) {
  body {
    background: brown;
  }
}

@media (max-width: 700px) {
  body {
    background: pink;
  }
}

@media (max-width: 600px) {
  body {
    background: blue;
  }
}

@media (max-width: 500px) {
  body {
    background: orange;
  }
}
```

> As mentioned earlier, it is possible to create an unlimited number of media queries for every possible screen size. However, it is best to minimize your media-query usage and rely more on the natural flexibility of your layouts.

#### Print Styles

However, it is possible to create a different set of styles for your website when it is sent to your printer or viewed in print-preview mode by using the print keyword.

```css
@media print {
  /* print styles go here! */
}
```
