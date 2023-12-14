# CSS Accessibility

## Keyboard Navigation

### Tab Order

The tab order is the order in which elements on the page will receive focus when pressing the `Tab` key, and is by default in the same order as the order of elements listed in the HTML file:

```html
<!-- This element is first in the tab order. -->
<div tabindex='0'>This is the first element listed in the HTML.</div>

<!-- This element is second in the tab order. -->
<div tabindex='0'>This is the second element listed in the HTML.</div>
```

> You may use, you should make sure the tab order matches the visual order of elements

> ❗ Give each individual item in that **hidden content** a **tabindex value of -1**, since that prevents an element from receiving focus via the keyboard

## Use Appropriate Semantics

- `<aside>`
- `<footer>`
- `<form>`
- `<header>`
- `<main>`
- `<nav>`
- `<section>`

## HTML Elements

### Links

```html
Visit <a href='...'>VIM</a> to have a cool text editor
```

### Images

Add `alt`

```html
<img src='...' alt='Vim logo picture' />
```

## Tools for Checking Accessibility on Website

https://chromewebstore.google.com/detail/axe-devtools-web-accessib/lhdoppojpmngadmnindnejefpokejbdd?hl=en-US&pli=1

https://developer.chrome.com/docs/lighthouse/overview/


### Dev Tools

https://developer.chrome.com/docs/devtools/accessibility/reference/#pane


