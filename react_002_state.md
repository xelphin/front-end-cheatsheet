# React State

```jsx
const [stateValue, setStateValue] = useState(initialValue);

// adapted for our use case:
const [backgroundColor, setBackgroundColor] = useState(initialColor);
```

## Use Case

Example where a variable isn't enough

```jsx
import { sculptureList } from './data.js';

export default function Gallery() {
  let index = 0;

  function handleClick() {
    index = index + 1;
  }

  let sculpture = sculptureList[index];
  return (
    <>
      <button onClick={handleClick}>
        Next
      </button>
      <h2>
        <i>{sculpture.name} </i> 
        by {sculpture.artist}
      </h2>
      <h3>  
        ({index + 1} of {sculptureList.length})
      </h3>
      <img 
        src={sculpture.url} 
        alt={sculpture.alt}
      />
      <p>
        {sculpture.description}
      </p>
    </>
  );
}
```

Instead you can use State:

```jsx
import { useState } from 'react';
import { sculptureList } from './data.js';

export default function Gallery() {
  const [index, setIndex] = useState(0);

  function handleClick() {
    setIndex(index + 1);
  }

  let sculpture = sculptureList[index];
  return (
    <>
      <button onClick={handleClick}>
        Next
      </button>
      <h2>
        <i>{sculpture.name} </i> 
        by {sculpture.artist}
      </h2>
      <h3>  
        ({index + 1} of {sculptureList.length})
      </h3>
      <img 
        src={sculpture.url} 
        alt={sculpture.alt}
      />
      <p>
        {sculpture.description}
      </p>
    </>
  );
}
```

When a `setState` is triggered (`setIndex`), then the whole component (`Gallery`) is re-rendered but with the updated state (`index`)

## Notice

### State should not be mutated

<details>
        <summary>Example</summary>

```jsx
function Person() {
  //    [state  , useState] 
  const [person, setPerson] = useState({ name: 'John', age: 100 });

  // BAD - Don't do this!
  const handleIncreaseAge = () =>{
    // mutating the current state object
    person.age = person.age + 1;
    setPerson(person);
  };

  // GOOD - Do this!
  const handleIncreaseAge = () =>{
    // copy the existing person object into a new object
    // while updating the age property
    const newPerson = { ...person, age: person.age + 1 };
    setPerson(newPerson);
  };

  return (
    <>
      <h1>{person.name}</h1>
      <h2>{person.age}</h2>
      <button onClick={handleIncreaseAge}>Increase age</button>
    </>
  );
}
```

In the above example, notice how we create a new object, and then copy the existing state values into the new object while providing a new value for `age`. That is because if we don’t provide a new object to `setState` it is not guaranteed to re-render the page. Therefore we should always provide a new Object for `setState` to trigger a re-render. `setState` uses `Object.is` to determine if the previous state is the same.

As for nested objects and arrays, state can get tricky fast since you will have to copy the nested items as well. Be careful when using them.
</details>

### State updater functions

<details>
        <summary>Example</summary>

```jsx
const handleIncreaseAge = () => {
  setPerson({ ...person, age: person.age + 1 });
  setPerson({ ...person, age: person.age + 1 });
};
```

> "Hey, replace the current render’s person with an increase in age by 1. Then, replace the current render’s person with an increase in age by 1."

Notice the word “replace”. When you pass in the value to the setState function, React will replace the current state with the value you passed in. You might be wondering, what if I want to update the state multiple times using the latest state? This is where the state updater function comes in.

```jsx
const handleIncreaseAge = () => {
  setPerson((prevPerson) => ({ ...prevPerson, age: prevPerson.age + 1 }));
  setPerson((prevPerson) => ({ ...prevPerson, age: prevPerson.age + 1 }));
};
```

</details>

### Controlled Component

<details>
        <summary>Example</summary>

```jsx
function CustomInput() {
  const [value, setValue] = useState('');

  return (
    <input
        type="text"
        value={value}
        onChange={(event) => setValue(event.target.value)}
    />
  );
}
```

Now, every time the user types something in the input, React will ensure you have the latest comment/review/post (whatever the user was typing) in `value`.
</details>

### Render depending on state

<details>
        <summary>Example</summary>

```jsx
import { useState } from 'react';

export default function Form() {
  const [isSent, setIsSent] = useState(false);
  const [message, setMessage] = useState('Hi!');
  if (isSent) {
    return <h1>Your message is on its way!</h1>
  }
  return (
    <form onSubmit={(e) => {
      e.preventDefault();
      setIsSent(true);
      sendMessage(message);
    }}>
      <textarea
        placeholder="Message"
        value={message}
        onChange={e => setMessage(e.target.value)}
      />
      <button type="submit">Send</button>
    </form>
  );
}

function sendMessage(message) {
  // ...
}
```

</details>