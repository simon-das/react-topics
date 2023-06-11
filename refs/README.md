# Refs
Refs in React provide a way to access and interact with the DOM or React elements directly. They are often used to capture references to specific elements or components in a React application.

## Key Points
1. When applying the ref attribute to an HTML element, the ref object created using React.createRef() will contain the corresponding DOM element as its current property.
2. When the ref attribute is used on a custom class component, the ref object will receive the instance of the component after it has been mounted, accessible through its current property.
3. Function components do not have instances, so the ref attribute cannot be used directly on them.

<br>

```jsx
import React, { useRef } from 'react';

function TextInput() {
  const inputRef = useRef(null);

  const handleClick = () => {
    // Accessing the input element using the ref
    inputRef.current.focus();
  };

  return (
    <div>
      <input ref={inputRef} type="text" />
      <button onClick={handleClick}>Focus Input</button>
    </div>
  );
}

function App() {
  return (
    <div>
      <h1>Using Refs in React</h1>
      <TextInput />
    </div>
  );
}

export default App;
```

<br>

## Reference
https://legacy.reactjs.org/docs/refs-and-the-dom.html
