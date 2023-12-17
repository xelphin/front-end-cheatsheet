# React Components

## Basic
1. Create component

// Greeting.jsx
```jsx
function Greeting() {
    return <h1>&quot;I swear by my pretty floral bonnet, I will end you.&quot;</h1>;
}
  
export default Greeting;
```

> Make sure to capitalize

2. Import it

// main.jsx
```jsx
// ...
import Greeting from './Greeting.jsx'

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <Greeting />
  </React.StrictMode>,
)
```

https://developer.mozilla.org/en-US/docs/web/javascript/reference/statements/export#description (Different ways to export)

## JSX

Can use converter (html -> JSX): https://transform.tools/html-to-jsx

<details>
        <summary>Common Syntax Rules</summary>

### Return a single root element 
If you wish to return multiple elements in a component, you can do so by wrapping them in a parent tag:

```jsx
function MyComponent() {
  return (
    <>
      <h1>Example h1</h1>
      <h2>Example h2</h2>
    </>
    // Could replace <></> (fragment) with <div></div> (div)
  );
}
```

### Closing Tags
In JSX, we must explicitly close and wrap these tags. 
`<input>` would become `<input />`, and `<li>` would become `<li></li>`

### camelCase most things

```jsx
    <>
      <div className="container">
        <svg>
          <circle cx="25" cy="75" r="20" stroke="green" strokeWidth="2" />
        </svg>
      </div>
    </>
```
</details>

### Passing variables with curly braces

```jsx
export default function Avatar() {
  const avatar = 'https://i.imgur.com/7vQD0fPs.jpg';
  const name = 'Gregorio Y. Zara';
    return (
        <div className="container">
            <img
            className="avatar"
            src={avatar}
            alt={name}
            />
            <h1>{name}'s To Do List</h1>
        </div>
    );
}
```

#### Also other javascript expressions

```jsx
const today = new Date();

function formatDate(date) {
  return new Intl.DateTimeFormat(
    'en-US',
    { weekday: 'long' }
  ).format(date);
}

export default function TodoList() {
  return (
    <h1>To Do List for {formatDate(today)}</h1>
  );
}
```

To pass objects you need to do doubly curly-braces, ex: `person={{ name: "Hedy Lamarr", inventions: 5 }}`

So with CSS styles for examples

```jsx
export default function TodoList() {
  return (
    <ul style={{
      backgroundColor: 'black',
      color: 'pink'
      }}>
      <li>Improve the videophone</li>
      <li>Prepare aeronautics lectures</li>
      <li>Work on the alcohol-fuelled engine</li>
    </ul>
  );
}
```

<details>
        <summary>Summarizing example</summary>

```jsx
const person = {
  name: 'Gregorio Y. Zara',
  theme: {
    backgroundColor: 'black',
    color: 'pink'
  }
};

export default function TodoList() {
  return (
    <div style={person.theme}>
      <h1>{person.name}'s Todos</h1>
      <img
        className="avatar"
        src="https://i.imgur.com/7vQD0fPs.jpg"
        alt="Gregorio Y. Zara"
      />
      <ul>
        <li>Improve the videophone</li>
        <li>Prepare aeronautics lectures</li>
        <li>Work on the alcohol-fuelled engine</li>
      </ul>
    </div>
  );
}
```

</details>

## Rendering Techniques

```jsx
function MyComponent() {
  const animals = ["Lion", "Cow", "Snake", "Lizard"];
  const animalsList = animals.map((animal) => <li key={animal}>{animal}</li>)

  return (
    <div>
      <h1>Animals: </h1>
      <ul>
        {animalsList}
      </ul>
    </div>
  );
}
```

<details>
        <summary>Can also do</summary>

```jsx
function MyComponent() {
  const animals = ["Lion", "Cow", "Snake", "Lizard"];

  return (
    <div>
      <h1>Animals: </h1>
      <ul>
        {animals.map((animal) => {
          return <li key={animal}>{animal}</li>;
        })}
      </ul>
    </div>
  );
}
```

</details>



### Using props

```jsx
function ListItem(props) {
  return <li>{props.animal}</li>
}

function List(props) {
  return (
    <ul>
      {props.animals.map((animal) => {
        return <ListItem key={animal} animal={animal} />;
      })}
    </ul>
  );
}

function MyComponent() {
  const animals = ["Lion", "Cow", "Snake", "Lizard"];

  return (
    <div>
      <h1>Animals: </h1>
      <List animals={animals} />
    </div>
  );
}
```

### Conditional Rendering

<details>
        <summary>See examples</summary>

```jsx
function List(props) {
  return (
    <ul>
      {props.animals.map((animal) => {
        return animal.startsWith("L") ? <li key={animal}>{animal}</li> : null;
      })}
    </ul>
  );
}

function MyComponent() {
  const animals = ["Lion", "Cow", "Snake", "Lizard"];

  return (
    <div>
      <h1>Animals: </h1>
      <List animals={animals} />
    </div>
  );
}
```

#### Using the && Operator

```jsx
function List(props) {
  return (
    <ul>
      {props.animals.map((animal) => {
        return animal.startsWith("L") && <li key={animal}>{animal}</li>;
      })}
    </ul>
  );
}

function MyComponent() {
  const animals = ["Lion", "Cow", "Snake", "Lizard"];

  return (
    <div>
      <h1>Animals: </h1>
      <List animals={animals} />
    </div>
  );
}
```

</details>

## Keys

You need to give each array item a key — a string or a number that uniquely identifies it among other items in that array.

```jsx
const todos = [
  { task: "mow the yard", id: uuid() },
  { task: "Work on Odin Projects", id: uuid() },
  { task: "feed the cat", id: uuid() },
];

function TodoList() {
  return (
    <ul>
      {todos.map((todo) => (
        // here we are using the already generated id as the key.
        <li key={todo.id}>{todo.task}</li>
      ))}
    </ul>
  );
}
```

> Keys should never be generated on the fly. Using `key={Math.random()}` or `key={uuid()}` while rendering the list defeats the purpose of the list, as now a new key will get created for every render of the list

#### Rules

1. Keys must be unique among siblings. However, it’s okay to use the same keys for JSX nodes in different arrays.
2. Keys must not change or that defeats their purpose! Don’t generate them while rendering.

## Passing Data Between Components

```jsx
function Button(props) {
  const buttonStyle = {
    color: props.color,
    fontSize: props.fontSize + 'px'
  };

  return (
    <button style={buttonStyle}>{props.text}</button>
  );
}

export default function App() {
  return (
    <div>
      <Button text="Click Me!" color="blue" fontSize={12} />
      <Button text="Don't Click Me!" color="red" fontSize={12} />
      <Button text="Click Me!" color="blue" fontSize={20} />
    </div>
  );
}
```

### Props Destructuring

<details>
        <summary>See example</summary>

```jsx
function Button({ text, color, fontSize }) {
  const buttonStyle = {
    color: color,
    fontSize: fontSize + "px"
  };

  return <button style={buttonStyle}>{text}</button>;
}

export default function App() {
  return (
    <div>
      <Button text="Click Me!" color="blue" fontSize={12} />
      <Button text="Don't Click Me!" color="red" fontSize={12} />
      <Button text="Click Me!" color="blue" fontSize={20} />
    </div>
  );
}
```

</details>        

### Default Props

Could do:

```jsx
Button.defaultProps = {
  text: "Click Me!",
  color: "blue",
  fontSize: 12
};

export default function App() {

  
  return (
    <div>
      <Button />
      <Button text="Don't Click Me!" color="red" />
      <Button fontSize={20} />
    </div>
  );
}
```

<details>
        <summary>Default Props and Props Destructuring</summary>

```jsx
function Button({ text = "Click Me!", color = "blue", fontSize = 12 }) {
  const buttonStyle = {
    color: color,
    fontSize: fontSize + "px"
  };

  return <button style={buttonStyle}>{text}</button>;
}
```

</details>

### Functions as props

Can also do:

```jsx
function Button({ text = "Click Me!", color = "blue", fontSize = 12, handleClick }) {
  const buttonStyle = {
    color: color,
    fontSize: fontSize + "px"
  };

  return (
    <button onClick={() => handleClick('https://www.theodinproject.com')} style={buttonStyle}>
      {text}
    </button>
  );
}

export default function App() {
  const handleButtonClick = (url) => {
    window.location.href = url;
  };

  return (
    <div>
      <Button handleClick={handleButtonClick} />
    </div>
  );
}
```

### Forwarding Props

Use spread syntax
```jsx
function Profile(props) {
  return (
    <div className="card">
      <Avatar {...props} />
    </div>
  );
}
```