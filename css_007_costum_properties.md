# CSS Costum Properties

## Using Costum Properties

```css
.error-modal {
  --color-error-text: red;
  --modal-border: 1px solid black;
  --modal-font-size: calc(2rem + 5vw);

  color: var(--color-error-text);
  border: var(--modal-border);
  font-size: var(--modal-font-size);
}
```

## Fallback Values
The first parameter we’ve already gone over, which is the custom property we want to assign. The second parameter is an optional fallback value. When a fallback value is provided in addition to a custom property, the fallback value will be used if the custom property is invalid or hasn’t been declared yet.
```css
.fallback {
  --color-text: white;

  background-color: var(--undeclared-property, black);
  color: var(--undeclared-again, var(--color-text, yellow));
}
```

## Scope

<details>
<summary>Scope Example</summary>

In the example below, only the element with the cool-paragraph class would get styled with a red background since it’s a descendant of the element where our custom property is declared.

```html
<div class='cool-div'>
  <p class='cool-paragraph'>Check out my cool, red background!</p>
</div>

<p class='boring-paragraph'>I'm not in scope so I'm not cool.</p>
```

```css
.cool-div {
  --main-bg: red;
}

.cool-paragraph {
  background-color: var(--main-bg);
}

.boring-paragraph {
  background-color: var(--main-bg);
}
```
</details>

### Root Selector
By declaring our custom property on the :root selector in the example below, we can access it on any other valid selector within our CSS file, since any other selector would be considered a descendant of the :root selector.
```css
:root {
  --main-color: red;
}
```

## Creating themes with custom properties

Can toggle between themes as shown below:

```html
<div class="container">
  <p>You're now viewing this example with the <span class='theme-name'>dark</span> theme!</p>
  <button class="theme-toggle">Toggle Theme</button>
</div>
```

```css
:root.dark {
  --border-btn: 1px solid rgb(220, 220, 220);
  --color-base-bg: rgb(18, 18, 18);
  --color-base-text: rgb(240, 240, 240);
  --color-btn-bg: rgb(36, 36, 36);
}

:root.light {
  --border-btn: 1px solid rgb(36, 36, 36);
  --color-base-bg: rgb(240, 240, 240);
  --color-base-text: rgb(18, 18, 18);
  --color-btn-bg: rgb(220, 220, 220);
}

body,
.theme-toggle {
  color: var(--color-base-text);
}

/* ... */
```

```js
function setTheme() {
  const root = document.documentElement;
  const newTheme = root.className === 'dark' ? 'light' : 'dark';
  root.className = newTheme;
  
  document.querySelector('.theme-name').textContent = newTheme;
}

document.querySelector('.theme-toggle').addEventListener('click', setTheme)
```

### Media Queries - prefers-color-scheme
Checks whether a user has selected a theme preference on their OS/user agent.

```css
:root {
  --border-btn: 1px solid rgb(36, 36, 36);
  --color-base-bg: rgb(240, 240, 240);
  --color-base-text: rgb(18, 18, 18);
  --color-btn-bg: rgb(220, 220, 220);
  --theme-name: "light";
}

@media (prefers-color-scheme: dark) {
  :root {
    --border-btn: 1px solid rgb(220, 220, 220);
    --color-base-bg: rgb(18, 18, 18);
    --color-base-text: rgb(240, 240, 240);
    --color-btn-bg: rgb(36, 36, 36);
    --theme-name: "dark";
  }
}

body {
  background-color: var(--color-base-bg);
  color: var(--color-base-text);
  padding: 10px;
}

/* ... */
```
<details>
<summary>Explanation</summary>

We first added custom properties on the :root element outside of the media query. This gives us a default theme in case a user doesn’t have a preference set on their OS or user agent, or if a browser doesn’t support the media query. In this case, we’re using our “light” theme colors as the default. Then we added a prefers-color-scheme media query for when a user has a dark theme set in their preferences.
</details>

<details>
<summary>NOTE</summary>

Need to be aware of a few things when it comes to using this media query:

- Only dark and light are valid values for the media query, so you can’t use it to implement any themes beyond these two basic ones.
- The light value for the media query is actually for when a user has a light theme specified or when they have no preference set.
- It doesn’t allow users to change the theme themselves, which can still be important in cases where a user might want to use the theme opposite of their OS/user agent preferred one for whatever reason.

</details>
