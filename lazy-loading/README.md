# Introduction
Lazy loading in React refers to a technique where components or assets are loaded asynchronously, typically when they are needed or requested by the user. It allows to split the 
application into smaller chunks and load them on-demand, rather than loading everything upfront.

Instead of loading the entire application or all components at once, lazy loading allows to load specific parts of the application when they are required. 
This can significantly improve the initial loading time of the application, especially for larger applications with complex components.

## Key Points
1. React will only initiate the loading process when it attempt to render the component for the first time.
2. Once React triggers the loading process, it will wait for it to complete, and then render the resulting value as a React component.
3. The Promise returned by the lazy loading function and its resolved value will both be cached, ensuring that React doesn't trigger the loading process multiple times.
4. If the Promise encounters an error, React will throw the error to be handled by the nearest Error Boundary.
5. By using a <Suspense> boundary to wrap the lazy component or its parent components, the content can be specified what should be displayed during the loading phase.
  
## Example
    import React, { lazy, Suspense } from 'react';

    const MyLazyComponent = lazy(() => import('./MyLazyComponent'));

    function App() {
      return (
        <div>
          <h1>My App</h1>
          <Suspense fallback={<div>Loading...</div>}>
            <MyLazyComponent />
          </Suspense>
        </div>
      );
    }

    export default App;
  
