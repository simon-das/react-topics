# Introduction
`useMemo` is a hook in React that allows you to optimize the performance of your component by memoizing the result of a function call. It's useful when you have a computationally expensive function or a value that is 
costly to compute, and you want to avoid re-computing it unnecessarily. It caches the result of a calculation between re-renders.


### Example
```jsx
import React, { useMemo } from 'react';

function MyComponent({ a, b }) {
  const result = useMemo(() => {
    // Expensive computation or value generation
    console.log('Computing result...');
    return a + b;
  }, [a, b]); // Dependencies: a and b

  return <div>{result}</div>;
}
```

<br>

1. `useMemo` allows you to skip expensive recalculations by caching the result of a function or value.
2. It helps in skipping the re-rendering of components when the dependencies of `useMemo` remain unchanged.
3. `useMemo` can be used to memoize a dependency of another hook, ensuring that the dependency is only re-evaluated when necessary.
4. It is useful for memoizing a function, ensuring that the function is only re-created when its dependencies change, improving performance.

<br>

## Reference
https://react.dev/reference/react/useMemo
