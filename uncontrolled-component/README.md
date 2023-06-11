# Uncontrolled Component
An uncontrolled component is a component where the form data is handled by the DOM itself, rather than by React. The component holds its own state internally and can update the DOM directly.

Uncontrolled components can be useful in certain cases where direct DOM manipulation is required or when integrating with third-party libraries.

<br>

```jsx
import React, { useRef } from 'react';

function UncontrolledComponent() {
  const inputRef = useRef(null);

  const handleSubmit = (event) => {
    event.preventDefault();
    console.log('Submitted value:', inputRef.current.value);
    // ... do something with the value
    inputRef.current.value = '';
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" ref={inputRef} />
      <button type="submit">Submit</button>
    </form>
  );
}
```

<br>

## Reference
https://legacy.reactjs.org/docs/uncontrolled-components.html
