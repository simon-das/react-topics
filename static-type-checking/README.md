# Static Type Checking
Static type checking in React refers to the practice of using a type system to verify and enforce the correctness of the types of variables, props, and function signatures within a React application at compile-time. It helps catch type-related errors early and improves code quality and maintainability.

Two recommend static type checkers Flow and TypeScript (instead of PropTypes) have been mentioned in the following.

## Flow
Flow is a static type checker for JavaScript that can be used with React to provide static type checking and inference. It helps catch type-related errors and provides type annotations to improve code quality and maintainability. By using Flow for static type checking, you can catch type-related errors early, improve code readability, and enhance the reliability of your React components.

1. Set up a new React project with Flow by installing the necessary dependencies:
```bash
npx create-react-app my-app
cd my-app
npm install --save-dev flow-bin
```

2. Initialize Flow in your project by running the following command in the project directory:
```bash
npm run flow init
```

3. Add type annotations to your React components, props, and state. For example, let's create a simple component that receives a prop of type string:
```javascript
// @flow
import React from 'react';

type GreetingProps = {
  name: string;
};

const Greeting = ({ name }: GreetingProps) => {
  return <div>Hello, {name}!</div>;
};

export default Greeting;
```

In this example, we use the `type` keyword to define the type `GreetingProps` to specify the expected prop `name` as a string.

4. Use the component and pass the props with the correct types:
```javascript
// @flow
import React from 'react';
import Greeting from './Greeting';

const App = () => {
  return <Greeting name="John" />;
};

export default App;
```

Here, we pass the prop `name` as a string to the `Greeting` component.

5. Run Flow in your project to perform static type checking by executing the following command:
```bash
npm run flow
```

Flow will analyze your code and provide type checking feedback. If there are any type errors, they will be reported in the terminal, highlighting the specific areas where type violations occur.

<br>

## TypeScript
Another popular tool for static type checking in React is TypeScript. By using TypeScript for static type checking, you can catch type-related errors early, improve code readability, and provide better documentation for your React components, props, and state.

1. Set up a new React project with TypeScript by running the following command:
```bash
npx create-react-app my-app --template typescript
```

2. Define the types for your components, props, and state. For example, let's create a simple component that receives a prop of type string:
```typescript
import React from 'react';

type GreetingProps = {
  name: string;
};

const Greeting: React.FC<GreetingProps> = ({ name }) => {
  return <div>Hello, {name}!</div>;
};

export default Greeting;
```

In this example, we define a type `GreetingProps` to specify the expected prop `name` as a string. The `React.FC` type is used to define the component type.

3. Use the component and pass the props with the correct types:
```typescript
import React from 'react';
import Greeting from './Greeting';

const App: React.FC = () => {
  return <Greeting name="John" />;
};

export default App;
```

Here, we pass the prop `name` as a string to the `Greeting` component.

4. TypeScript will analyze the code and provide compile-time type checking. If there are any type errors, they will be reported during the build process, preventing potential runtime issues.

<br>

## Reference
https://legacy.reactjs.org/docs/static-type-checking.html
