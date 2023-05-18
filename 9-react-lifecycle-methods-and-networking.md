# React Lifecycle Methods and Networking

| Term | Definition |
| ---- | ---------- |
| __Component lifecycle__ | The series of phases a React component goes through, including mounting, updating, and unmounting, during its existence in the DOM. |
| __Lifecycle methods__ | Methods provided by React that allow you to hook into different phases of a component's lifecycle, such as `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount`. |
| __Mounting onto the DOM__ | The process of a component being rendered and added to the DOM for the first time. |

---

## Using `useEffect` to run code when a component has mounted

- What is the import retrieving when it calls `React, { useEffect} from 'react'`?
- How is `useEffect` related to `useState`, if at all?
- What does it mean for a component to `mount`?
- What does the empty array `[]` represent in the `useEffect` function? Why is it empty?

```js
import React, { useEffect } from 'react';

function MyComponent() {
  useEffect(() => {
    // Code to be executed after component has mounted
    console.log('Component has mounted');
  }, []);

  // Component render
  return <div>My Component</div>;
}
```

## Using the dependency array inside of `useEffect` to propagate data changes to the view

- What is the default value of our `count` state?
- When will the `useEffect` hook be called in this component?
- If we had another state variable in this function, would the `useEffect` run when that changed as well?
- What event is causing the `count` to change?
- Where will we see the changes to `count`?

```js
import React, { useEffect, useState } from 'react';

function MyComponent() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log('Count has changed:', count);
  }, [count]);

  const incrementCount = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={incrementCount}>Increment</button>
    </div>
  );
}
```

## Using `useEffect` to make a fetch request on component load

- When will this `fetch` request happen?
- How often does the `fetch` request happen?
- What does the interface show _before_ the request is complete?
- What does the interface show _after_ the request is complete?

```js
import React, { useEffect, useState } from 'react';

function MyComponent() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then(response => response.json())
      .then(data => setData(data));
  }, []);

  return (
    <div>
      {data ? (
        <div>
          <h2>Data:</h2>
          <pre>{JSON.stringify(data, null, 2)}</pre>
        </div>
      ) : (
        <p>Loading data...</p>
      )}
    </div>
  );
}
```

## Multiple useEffects

- What would happen if we ran the `bad` example?
- When is it a good time to use multiple useEffects?

```js
// Good
useEffect(() => {
  getOrderInfo();
}, [orderInfo]);

useEffect(() => {
  getUser();
}, [user]);

// Bad
useEffect(() => {
  getOrderInfo();
  getUser();
}, [orderInfo, user]);

```