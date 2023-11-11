# CSS Positioning

## Flexbox

```html
<div class="flex-container">
  <div class="flex-item" id="item1"></div>
  <div class="flex-item" id="item2"></div>
  <div class="flex-item" id="item3"></div>
</div>
```

```css
.flex-container {
  /* ... */
  display: flex;
  flex-direction: column-reverse;   /* vertical/horizontal */
  flex-wrap: wrap;                  /* single/multi line*/
  justify-content: center;          /* relative positioning*/
  align-items: stretch;             /* place in container */
  align-content: flex-end;          /* like justify-content but in other axis*/
}

#item1{
    align-self: baseline;
    flex: 1 0 30%;                  /* flex-grow / flex-shrink / flex-basis */
}
```

<details>
<summary>display</summary>

- ```flex``` apply flex (as block)
- ```inline-flex``` apply flex as inline
</details>

<details>
<summary>flex-direction</summary>

- ```row``` 
- ```row-reverse```
- ```column``` 
- ```column-reverse```
</details>

<details>
<summary>flex-wrap</summary>

- ```nowrap``` In single line 
- ```wrap``` multi-line
- ```wrap-reverse``` 
</details>

<details>
<summary>justify-content</summary>

- ```flex-start``` compressed together at start
- ```flex-end``` compressed together at end
- ```flex-center``` compressed together at center
- ```space-between```
- ```space-around```
- ```space-evenly```
</details>

<details>
<summary>align-items</summary>

- ```stretch``` 
- ```flex-start```
- ```flex-end```
- ```center```
- ```baseline```
- ```auto```
</details>

<details>
<summary>align-content</summary>

- ```stretch``` 
- ```flex-start```
- ```flex-end```
- ```center```
- ```space-between```
- ```space-around```
</details>

## Overflow
```css
overflow: visible;
```
<details>
<summary>overflow</summary>

- ```visible``` 
- ```hidden```
- ```clip```
- ```scroll```
- ```auto```
</details>

## Float

```css
float: left;
```
<details>
<summary>float</summary>

- ```left``` 
- ```right```
- ```none```
- ```inherit```
</details>

## Position

```css
position: relative;
left: 30px;
```
<details>
<summary>relative</summary>

- ```static``` 
always positioned according to the normal flow of the page
- ```relative```
positioned relative to its normal position
- ```fixed```
positioned relative to the viewport, which means it always stays in the same place even if the page is scrolled
- ```absolute```
positioned relative to the nearest positioned ancestor (instead of positioned relative to the viewport, like fixed)
- ```sticky```
positioned based on the user's scroll position
</details>

## Z-Index
Bring forwards/backwards

```css
z-index: -2;
```