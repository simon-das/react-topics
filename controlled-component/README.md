# Controlled Component
A controlled component in React is a component where the state is managed by React itself. The component receives its current value and any updates to that value via props. It doesn't have its own internal state that it 
manages. The parent component has full control over the value and behavior of the controlled component.

<br>

```jsx
import React, { useState } from 'react';

function ControlledComponent() {
  const [value, setValue] = useState('');

  const handleChange = (event) => {
    setValue(event.target.value);
  };

  return (
    <input type="text" value={value} onChange={handleChange} />
  );
}
```

<br>

## Reference
https://legacy.reactjs.org/docs/forms.html#controlled-components
