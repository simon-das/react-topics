# Render Props
The render props pattern in React is a technique where a component receives a function as a prop, which it can then call and render with data to provide to its children. This pattern allows for dynamic composition 
of components and the sharing of logic between them.

## Key Points
1. A render prop is a function prop that a component uses to know what to render.
2. Any prop that is a function that a component uses to know what to render is technically a “render prop”. It's not mandatory to use a prop named **render** to use this pattern.
3. Children prop do the same as render.

<br>

```jsx
import React from 'react';

// A component that uses render props
class MouseTracker extends React.Component {
  state = { x: 0, y: 0 };

  handleMouseMove = (event) => {
    this.setState({ x: event.clientX, y: event.clientY });
  };

  render() {
    return (
      <div onMouseMove={this.handleMouseMove}>
        {this.props.render(this.state)}
      </div>
    );
  }
}

// A component that renders the mouse coordinates
class MouseCoordinates extends React.Component {
  render() {
    return (
      <MouseTracker
        render={(mousePosition) => (
          <div>
            Mouse coordinates: {mousePosition.x}, {mousePosition.y}
          </div>
        )}
      />
    );
  }
}

// Usage
function App() {
  return <MouseCoordinates />;
}

export default App;
```

<br>

## Reference
https://legacy.reactjs.org/docs/render-props.html
