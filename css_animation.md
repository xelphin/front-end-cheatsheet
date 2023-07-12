# CSS Animation

## Transform

function(horizontal, vertical);

```css
transform: translate(5%, 20px);             /* Move */
transform: rotate(20deg);                   /* Rotate */
transform: scale(1.5, 2);                   /* Size */
transform: skew(20deg, 10deg);              /* Skew */
transform: matrix(1, -0.3, 0, 1, 0, 0);     /* Skew */
```
## Transition

```css
#my-object {
    transition-property: width ,height;
    transition-duration: 1s,1.5s;
    transition-timing-function: linear,ease;
    transition-delay: 0.2s,0.1s;

    /* shorthand */
    transition: background-color 2s ease-in 0s;
}

#my-object:hover {

  height: 20vh;
  width: 80px;

  background-color: var(--orange);
}
```

## Animation

```css
@keyframes animation_1 {
  0% {background-color:antiquewhite; left:10px; top:20px;}
  60% {background-color:chocolate; left:40px; top:30px;}
  100% {background-color: #c48ca1; left:0px; top:0px;}
}

#my-object {
  position: relative;
  animation-name: animation_1;
  animation-delay: 2s;
  animation-duration: 6s;
  animation-iteration-count: 3;
  animation-timing-function: ease-in;
}
```
