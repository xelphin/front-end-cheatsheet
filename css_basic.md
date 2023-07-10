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