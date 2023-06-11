# MobX
MobX is a state management library that provides a simple and reactive approach to managing state in React applications. It allows you to create observable state objects and automatically tracks changes to them, ensuring that your components are updated when the state changes.

<br>

```jsx
import React from 'react';
import { observable, action } from 'mobx';
import { observer } from 'mobx-react';

// Create an observable state object
const counterState = observable({
  count: 0,
  
  // Define an action to update the count
  increment: action(function() {
    this.count += 1;
  }),
});

// Create a component that observes the state changes
const Counter = observer(() => (
  <div>
    <h2>Count: {counterState.count}</h2>
    <button onClick={counterState.increment}>Increment</button>
  </div>
));

export default Counter;
```
