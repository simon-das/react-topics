# Error Boundaries
The default behavior of React is to remove the UI from the screen if an error occurs during rendering. To prevent this, a part of the UI can be wrapped in an error boundary. An error boundary is a special component that allows displaying fallback UI instead of the crashed part, such as an error message.

To implement an error boundary component, the static method `getDerivedStateFromError` needs to be provided, which enables updating the state in response to an error and displaying an error message to the user. 
Optionally, `componentDidCatch` can be implemented to include additional logic, like logging the error to an analytics service.

    class ErrorBoundary extends React.Component {
      constructor(props) {
        super(props);
        this.state = { hasError: false };
      }

      static getDerivedStateFromError(error) {
        // Update state so the next render will show the fallback UI.
        return { hasError: true };
      }

      componentDidCatch(error, info) {
        // Example "componentStack":
        //   in ComponentThatThrows (created by App)
        //   in ErrorBoundary (created by App)
        //   in div (created by App)
        //   in App
        logErrorToMyService(error, info.componentStack);
      }

      render() {
        if (this.state.hasError) {
          // You can render any custom fallback UI
          return this.props.fallback;
        }

        return this.props.children;
      }
    }
    
 A part of the component tree can be wrapped with it
    
    <ErrorBoundary fallback={<p>Something went wrong</p>}>
      <Profile />
    </ErrorBoundary>
 
 
If an error is thrown by the Profile component or its child component, the ErrorBoundary will intercept the error, display a fallback UI with the provided error message, and send a production error report to the error reporting service.

It is not necessary to wrap each component in a separate error boundary. When considering the granularity of error boundaries, the placement of an error message should be taken into account. For example, in a messaging app, it is appropriate to have an error boundary around the list of conversations and individual messages. However, it would not be suitable to have a boundary around each avatar.
 

## Reference
https://react.dev/reference/react/Component#catching-rendering-errors-with-an-error-boundary
