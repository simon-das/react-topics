# Portals
Portals in React provide a way to render components into a DOM node that is outside the normal parent-child hierarchy of components. It allows you to render a component's content at a different position in the DOM tree, typically at the root or a specific container element.

To create a portal in React, you can use the `ReactDOM.createPortal` method. It takes two arguments: the content you want to render and the DOM element where you want to render it.

By using portals, we can render components outside the normal parent-child hierarchy. This can be useful for scenarios such as modals, tooltips, or any other case where you need to render content in a different part of the DOM tree while maintaining the component's functionality and state.

When you use a portal to render a component, it changes where the component appears in the HTML document, but it doesn't change how the component behaves. The component can still access the context provided by its parent and events will still work the same way. The only thing that's different is where the component is placed in the document.

<br>

```jsx
import ReactDOM from 'react-dom';

// Create a Portal component
const PortalComponent = () => {
  return ReactDOM.createPortal(
    <div className="portal-content">
      This content is rendered outside the root element.
    </div>,
    document.getElementById('portal-container')
  );
};

// Render the Portal component within the main app component
const App = () => {
  return (
    <div>
      <h1>Main App Content</h1>
      <div id="portal-container"></div>
      <PortalComponent />
    </div>
  );
};

// Render the main app component
ReactDOM.render(<App />, document.getElementById('root'));
```

<br>

## Reference
https://react.dev/reference/react-dom/createPortal
