# Bootstrap in React

| Term | Definition |
| ---- | ---------- |
| __CSS Framework__ | A pre-written code library or framework that provides solutions to common CSS problems and helps maintain consistency, responsiveness, and modern styling in web projects. |
| __Bootstrap__ | A popular open-source CSS framework initially developed at Twitter, providing a wide range of pre-designed CSS styles, components, and utilities for building responsive web applications. |
| __CDN (Content Delivery Network)__ | A network of servers distributed geographically that delivers web content, including CSS files, to users more efficiently by serving them from the server closest to the user. |

---

## Adding Bootstrap CSS link in `public/index.html`

- Why do we add this link to the `public/index.html` file instead of the `index.js` or `App.js` files?

```html
<head>
  ...
  <link
    rel="stylesheet"
    href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css"
    integrity="..."
    crossorigin="anonymous"
  />
</head>
```

## Example usage of Bootstrap CSS classes in a React component

- What is a `container` as it relates to page layouts?
- What does the `btn-primary` class do?

```js
import React from 'react';

const MyComponent = () => {
  return (
    <div className="container">
      <h1 className="display-4">Hello, Bootstrap!</h1>
      <button className="btn btn-primary">Click Me</button>
    </div>
  );
};

export default MyComponent;

```

## Bootstrap Grid

- What display property is the Bootstrap grid built on?
- What's the relationship between the `container`, `row`, and `col-md-4`?
- How would we break down the `col-md-4` class?
- How many columns is the Bootstrap grid based on?
- How would we nest grids in Bootstrap?

```js
import React from 'react';

const BootstrapGridExample = () => {
  return (
    <div className="container">
      <h1>Bootstrap CSS Grid Example</h1>
      <div className="row">
        <div className="col-md-4">
          <div className="card">
            <div className="card-body">
              <h5 className="card-title">Card 1</h5>
              <p className="card-text">Some text for Card 1.</p>
            </div>
          </div>
        </div>
        <div className="col-md-4">
          <div className="card">
            <div className="card-body">
              <h5 className="card-title">Card 2</h5>
              <p className="card-text">Some text for Card 2.</p>
            </div>
          </div>
        </div>
        <div className="col-md-4">
          <div className="card">
            <div className="card-body">
              <h5 className="card-title">Card 3</h5>
              <p className="card-text">Some text for Card 3.</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  );
};

export default BootstrapGridExample;
```