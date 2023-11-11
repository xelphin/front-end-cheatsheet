# CSS Functions

Example:

```css
color: rgb(0, 42, 255);
background: linear-gradient(90deg, blue, red);
```

## calc()

```css
:root {
	--header: 3rem;
	--footer: 40px;
	--main: calc(100vh - calc(var(--header) + var(--footer)));
}
```

## min()

Pick min from values in parenthesis
```css
width: min(150px, 100%);
```

## max()

Pick max from values in parenthesis
```css
width: max(100px, 4em, 50%);
```

## clamp()

```css
font-size: clamp(320px, 80vw, 60rem);
```

- the smallest value (320px)
- the ideal value (80vw)
- the largest value (60rem)

## Other

https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Functions
