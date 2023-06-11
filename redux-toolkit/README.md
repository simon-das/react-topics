# Redux Toolkit
Redux Toolkit is a library that provides utilities and abstractions to simplify the development of Redux applications. It includes features like simplified configuration, standardized Redux patterns, and built-in support for common Redux use cases.

By using Redux Toolkit, developers can write Redux code more efficiently and with fewer boilerplate, making it easier to manage state in complex applications.

Here's an example of using Redux Toolkit:

1. Install Redux Toolkit:
```
npm install @reduxjs/toolkit
```

2. Create a Redux store using `configureStore` from Redux Toolkit:
```javascript
import { configureStore } from '@reduxjs/toolkit';
import counterReducer from './counterSlice';

const store = configureStore({
  reducer: {
    counter: counterReducer,
  },
});

export default store;
```

3. Create a slice using `createSlice` from Redux Toolkit:
```javascript
import { createSlice } from '@reduxjs/toolkit';

const counterSlice = createSlice({
  name: 'counter',
  initialState: 0,
  reducers: {
    increment: (state) => state + 1,
    decrement: (state) => state - 1,
  },
});

export const { increment, decrement } = counterSlice.actions;
export default counterSlice.reducer;
```

4. Use the Redux store and actions in your components:
```javascript
import React from 'react';
import { useDispatch, useSelector } from 'react-redux';
import { increment, decrement } from './counterSlice';

const Counter = () => {
  const count = useSelector((state) => state.counter);
  const dispatch = useDispatch();

  const handleIncrement = () => {
    dispatch(increment());
  };

  const handleDecrement = () => {
    dispatch(decrement());
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={handleIncrement}>Increment</button>
      <button onClick={handleDecrement}>Decrement</button>
    </div>
  );
};

export default Counter;
```

In this example, Redux Toolkit simplifies the process of setting up the Redux store and defining reducers. The `configureStore` function sets up the store with the `counterReducer` defined using `createSlice`. The `createSlice` function generates action creators and a reducer based on the provided configuration. The `useSelector` hook allows components to access the Redux state, and the `useDispatch` hook provides a way to dispatch actions.

<br>

## APIs
1. `configureStore`: This API is used to create a Redux store with sensible defaults and configurations. It combines several Redux store setup steps into a single function call. You can provide a reducer object, middleware, and other options to customize the store setup.

2. `createSlice`: This API generates action creators and a reducer based on a provided configuration object. It helps in writing concise and predictable Redux code by reducing the amount of boilerplate code required. The configuration object includes the slice name, initial state, and an object with reducer functions for different actions.

3. `createAsyncThunk`: This API simplifies handling asynchronous actions in Redux. It generates an action creator that dispatches multiple actions during the different stages of an asynchronous operation (e.g., pending, fulfilled, rejected). It can be used with APIs like `axios` or `fetch` to handle data fetching and other async operations.

4. `createEntityAdapter`: This API is used to simplify the management of normalized data in the Redux store. It provides utility functions to work with entities and collections, such as adding, updating, and removing entities. It also generates selectors for querying and manipulating the normalized data.

5. `createReducer`: This API allows you to define a reducer function using a "builder callback" syntax. It provides a simpler and more readable way to handle complex reducer logic, including conditional logic, immutability, and handling different action types.

6. `createSelector`: This API is used to create memoized selectors for efficiently computing derived data from the Redux store. Memoized selectors cache the results and only recalculate when the input state changes. It helps in optimizing the performance of your application by avoiding unnecessary computations.

7. `createAction`: This API generates a simple action creator function that returns an action object with a specified type and payload. It helps in creating concise and readable action creators without writing the entire action object manually. The API takes a string parameter representing the action type and an optional payload creator function.

<br>

## Reference
https://redux-toolkit.js.org/introduction/getting-started
