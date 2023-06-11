# State Lifting
State lifting is a pattern in React where the state that is shared by multiple components is moved to a common parent component. This allows the parent component to manage and control the shared state, and pass it down to the child components as props.

State lifting is useful when multiple components need to share and synchronize the same state. It promotes better data flow and allows for centralized control of the shared state.

<br>

```jsx
import React, { useState } from 'react';

function ParentComponent() {
  const [count, setCount] = useState(0);

  const incrementCount = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <ChildComponent count={count} incrementCount={incrementCount} />
      <OtherChildComponent count={count} />
    </div>
  );
}

function ChildComponent({ count, incrementCount }) {
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={incrementCount}>Increment</button>
    </div>
  );
}

function OtherChildComponent({ count }) {
  return <p>Count: {count}</p>;
}
```

<br>

## Reference
https://react.dev/learn/sharing-state-between-components
