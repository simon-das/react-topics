# Code Splitting
Code splitting is a technique used in React to split a large bundle of JavaScript code into smaller, more manageable chunks. It helps improve performance by loading only the necessary code when it's required, rather than loading the entire bundle upfront.

Code splitting is particularly useful when you have large components or dependencies that are not required on the initial render but may be needed later, such as in response to user actions. It allows for more efficient resource utilization and helps improve the user experience.

<br>

```jsx
import React, { lazy, Suspense } from 'react';

const MyComponent = lazy(() => import('./MyComponent'));

function App() {
  return (
    <div>
      <h1>Code Splitting Example</h1>
      <Suspense fallback={<div>Loading...</div>}>
        <MyComponent />
      </Suspense>
    </div>
  );
}

export default App;
```

<br>

## Reference
https://legacy.reactjs.org/docs/code-splitting.html
