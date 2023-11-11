# CSS Text Properties

## Color General

```css
color: #1100ff;             /* hex */
color: rgb(100, 0, 127);    /* rgb */
color: hsl(15, 82%, 56%);   /* hsl */
color: darkgoldenrod;       /* name */
```

## Text Color

```css
color: rgb(100, 0, 127);
background-color: lightgrey;
```

## Font

```css
font-family: "Times New Roman", sans-serif;     /* font */
font-weight: 700;                               /* boldness */
font-size: 22px;                                /* size */
text-align: center;                             /* alignment */
```



<details>
<summary>Importing Fonts</summary>

Font Libraries:
- https://fonts.google.com/
- https://fontlibrary.org/en/catalogue

---

#### Method 1
In html
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Roboto&display=swap" rel="stylesheet">
```
---
#### Method 2
In css
```css
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');
```

---
#### Method 3
Installed font
```css
@font-face {
  font-family: my-cool-font;
  src: url(../fonts/the-font-file.woff);
}
```
Browsers and the font file formats they support:
https://www.w3schools.com/css/css3_fonts.asp

---

Then use in css as such

```css
body {
  font-family: 'Roboto', sans-serif;
}
```

</details>

## Align

```css
text-align: center;         /* horizontal alignment */
vertical-align: baseline;   /* vertical alignment */
```

<details>
        <summary>Options: text-align</summary>

- ```center```
- ```left```
- ```right```
- ```justify```: each line is stretched so that every line has equal width, and the left and right margins are straight
</details>
<details>
        <summary>Options: vertical-align</summary>

- ```baseline```
- ```text-top```
- ```text-bottom```
- ```sub```
- ```super```
</details>

## Shadow

```css
text-shadow: -1px 0 black, 0 1px black, 1px 0 black, 0 -1px black;
```

## Overflow (...)

```css
.truncate {
  width: 250px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
```

## Other

```css
h1 {
  font-style: italic;
  letter-spacing: .5em;
  line-height: 1.5;
  text-transform: capitalize; /*uppercase/lowercase/none/full-width/full-size-kana*/
}
```