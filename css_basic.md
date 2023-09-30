# CSS Basic

## Connect Stylesheet

```html
<!-- index.html -->

<head>
  <link rel="stylesheet" href="./mystyle/styles.css" />
</head>
```

## Inline CSS
(No need for a link)

```html
<body>
  <div style="color: white; background-color: black;">...</div>
</body>
```

## Define Variables In CSS

```css
:root {
  --dark: #202C39;
  --dark-blue: #283845;
  --brown: #B8B08D;
  --light: #F2D492;
  --orange: #F29559;
  --blue-opacity:#2838453f;
  --light-opacity:rgba(242, 212, 146, 0.397);
}
```

Use them
```css
color:var(--dark);
```

## Reset Stylesheet
Get rid of the default styling

<details>
<summary>meyerweb</summary>

```css
/* http://meyerweb.com/eric/tools/css/reset/ 
   v2.0 | 20110126
   License: none (public domain)
*/

html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed, 
figure, figcaption, footer, header, hgroup, 
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
	margin: 0;
	padding: 0;
	border: 0;
	font-size: 100%;
	font: inherit;
	vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure, 
footer, header, hgroup, menu, nav, section {
	display: block;
}
body {
	line-height: 1;
}
ol, ul {
	list-style: none;
}
blockquote, q {
	quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
	content: '';
	content: none;
}
table {
	border-collapse: collapse;
	border-spacing: 0;
}

```

</details>

## Units

- Absolute: ```px```
- Relative: ```rem``` -> 1rem is font size of root, ```em``` -> 1em is font size of parent
- Viewport: ```vh```-> equal to 1% of the viewport height and, ```vw``` -> equal to 1% of the viewport width

## Background

```css
body {
  background: green;
  background: content-box radial-gradient(crimson, skyblue);
  background: no-repeat url("../../media/examples/lizard.png");
  background: left 5% / 15% 60% repeat-x url("../../media/examples/star.png");
  background: center / contain no-repeat url("../../media/examples/firefox-logo.svg"),
            #eee 35% url("../../media/examples/lizard.png");
}
```