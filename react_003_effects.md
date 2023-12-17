# React Effects

## useEffect

```jsx
useEffect(() => {
  // This runs after every render
});

useEffect(() => {
  // This runs only on mount (when the component appears)
}, []);

useEffect(() => {
  // This runs on mount *and also* if either a or b have changed since the last render
}, [a, b]);
```
#### General Example
```jsx
import React, { useEffect, useState } from "react";

export default function Clock() {
  const [counter, setCounter] = useState(0);

  useEffect(() => {
    const key = setInterval(() => {
      setCounter(count => count + 1)
    }, 1000);

    return () => {
        // To avoid issue with the counter updating twice every second
      clearInterval(key);
    };
  }, [])

  return (
    <p>{counter} seconds have passed.</p>
  );
}
```
We pass an empty array in this example because we do not want the `useEffect` hook to run anytime other than the initial component render.

<details>
        <summary>Other Examples</summary>

```jsx
const serverUrl = 'https://localhost:1234';

function ChatRoom({ roomId }) {
  useEffect(() => {
    const connection = createConnection(serverUrl, roomId);
    connection.connect();
    return () => {
      connection.disconnect();
    };
  }, [roomId]);
  // ...
}
```
When the roomId prop has changed, so what your Effect did back then no longer matches the UI.

At this point, you want React to do two things:

1. Stop synchronizing with the old roomId (disconnect from the "prevRoom" room)
2. Start synchronizing with the new roomId (connect to the "currRoom" room)


</details>

### Used for

`useEffect` is a mechanism outside the concepts that React usually applies, allowing you to sync your component with various external systems like a server, API, or browser DOM. The single question that you can ask yourself before you use an effect is if there are any such external systems that need to be synced with, apart from props or state. Unnecessary `useEffect` hooks are code-smell, error-prone, and cause unnecessary performance issues.

<details>
        <summary>Examples where it's unecessary to use it</summary>

```jsx
import React, { useState } from "react";

export default function AdditionDisplay() {
  const [number1, setNumber1] = useState(0);
  const [number2, setNumber2] = useState(0);

  // This is all unnecessary.

  // const [sum, setSum] = useState(0);
  // useEffect(() => {
  //   setSum(number1 + number2);
  // }, [number1, number2]);

  const sum = number1 + number2;

  return (
    <p>{number1} + {number2} = {sum}</p>
  );
}
```

```jsx
import React, { useState } from "react";

export default function App() {
  const [input, setInput] = useState("");

  const handleInput = (e) => {
    setInput(e.target.value);
  };

  // You should avoid direct manipulation when not necessary

  // useEffect(() => {
  //   document.getElementById("name").addEventListener("change", handleInput);
  //   return () => {
  //     document.getElementById("name").removeEventListener("change", handleInput);
  //   }
  // });

  return (
    <>
      {/* <input id="name" /> */}

      <input onChange={handleInput} value={input} />
      <p>{ input }</p>
    </>
  );
}
```
</details>

### Avoiding Infinite Loops

```jsx
import { useEffect, useState } from 'react';

function CountInputChanges() {
  const [value, setValue] = useState('');
  const [count, setCount] = useState(-1);

  // BAD
  useEffect(() => setCount(count + 1), [value]); // Causes infinite loop

  const onChange = ({ target }) => setValue(target.value);

  return (
    <div>
      <input type="text" value={value} onChange={onChange} />
      <div>Number of changes: {count}</div>
    </div>
  );
}
```
`setCount()` rerenders the component. `useEffect()` without any dependencies, runs after every render. So `useEffect()` runs calling `setCount()` which rerenders calling the `useEffect()` and... You get an infinite loop.


Fix by doing:

```jsx
useEffect(() => setCount(count + 1), [value]);
```

By adding `[value]` as a dependency of `useEffect(..., [value])`, the `count` state variable will only be updated when `[value]` changes. This solves the infinite loop.

#### Other solutions

useRef()
```jsx
import { useState, useRef } from 'react';

function CountInputChanges() {
  const [value, setValue] = useState('');
  const countRef = useRef(0);

  const onChange = ({ target }) => {
    setValue(target.value);
    countRef.current++;
  };

  return (
    <div>
      <input type="text" value={value} onChange={onChange} />
      <div>Number of changes: {countRef.current}</div>
    </div>
  );
}
```
Updating a reference doesn't trigger re-rendering of the component.