# useRef
`useRef` is a Hook in React that allows you to create a mutable reference that persists across renders. It provides a way to store and access a value that won't cause a re-render when it changes.

<br>

```jsx
import { useRef } from 'react';

function MyComponent() {
  const countRef = useRef(0);

  const handleClick = () => {
    countRef.current += 1;
    console.log(countRef.current);
  };

  return (
    <div>
      <button onClick={handleClick}>Increment</button>
    </div>
  );
}
```

<br>

1. **Referencing a value with a ref**: `useRef` allows you to create a reference to a value that persists between renders without triggering re-renders. It's useful for storing information that doesn't affect the visual output of your component, such as interval IDs or previous values.

2. **Manipulating the DOM with a ref**: `useRef` can be used to directly access and manipulate DOM elements. You can assign the ref to an HTML element and then use the `current` property to interact with its properties and methods, like focusing an input or measuring its dimensions.

3. **Avoiding recreating the ref contents**: Since `useRef` returns the same ref object on subsequent renders, you can use it to prevent unnecessary recreations of the values stored within the ref. This is helpful when working with dependencies in other hooks or when passing refs as dependencies to useCallback or useEffect, ensuring stable references.

<br>

## Reference
https://react.dev/reference/react/useRef
