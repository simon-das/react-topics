# Event Switch
The Event Switch pattern in React is a technique used to handle multiple events or actions within a single component by 
conditionally rendering different event handlers based on a specific event type. It allows for efficient event handling and cleaner code organization.

This pattern is commonly used in managing states of reducer.

<br>

```jsx
import React, { useState } from 'react';

const Button = ({ onClick }) => (
  <button onClick={onClick}>Click me</button>
);

const EventSwitch = () => {
  const [count, setCount] = useState(0);

  const handleIncrement = () => {
    setCount(count + 1);
  };

  const handleDecrement = () => {
    setCount(count - 1);
  };

  const handleReset = () => {
    setCount(0);
  };

  const renderEventHandlers = () => {
    switch (count) {
      case 0:
        return {
          eventHandler: handleIncrement,
          buttonText: 'Increment',
        };
      case 10:
        return {
          eventHandler: handleDecrement,
          buttonText: 'Decrement',
        };
      default:
        return {
          eventHandler: handleReset,
          buttonText: 'Reset',
        };
    }
  };

  const { eventHandler, buttonText } = renderEventHandlers();

  return (
    <div>
      <h2>Count: {count}</h2>
      <Button onClick={eventHandler} buttonText={buttonText} />
    </div>
  );
};

// Usage
function App() {
  return <EventSwitch />;
}

export default App;
```
