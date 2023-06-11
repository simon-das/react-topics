# Fragment
React Fragment is a built-in component in React that allows you to group multiple elements without introducing an extra wrapping element in the DOM. It's useful when you want to return multiple elements from a 
component's render method without adding a container element.

Often used via <>...</> syntax.

<br>

```jsx
import React from 'react';

function MyComponent() {
  return (
    <React.Fragment>
      <h1>Title</h1>
      <p>Paragraph 1</p>
      <p>Paragraph 2</p>
    </React.Fragment>
  );
}
```

<br>

## Reference
https://react.dev/reference/react/Fragment
