# React Lifecycle Methods and Networking

| Term | Definition |
| ---- | ---------- |
| __Routing__ |  The process of determining how an application responds to a specific URL or route. |
| __Router__ | A component or library that manages the routing in a React application. |
| __React Router__ | A library that allows you to add routing functionality to your React applications, enabling multiple views and browser functionality like navigation using URLs. |

---

## Set Up React Router DOM

- What is the import `BrowserRouter as Router` doing?
- What does wrapping the app in `Router` do?

```js
import { BrowserRouter as Router, Route, Routes } from "react-router-dom";

// Wrapping the app in Router
function App() {
  return (
    <div className="App">
      <Router>
        <Header />
        <div className="wrapper">
          <Nav />
          <main>
            <Home />
            <About />
            <Newsletter />
            <ProductList products={lamps} type={"Lamps"} />
            <ProductList products={candles} type={"Candles"} />
          </main>
        </div>
        <Footer />
      </Router>
    </div>
  );
}
```

## Making Separate Views for Pages

- What does the `Routes` component do when the location changes?
- What does the `path` refer to?
- What is the `element` responsible for rendering?

```js
<main>
  <Routes>
    <Route path="/" element={<Home />} />
    <Route path="/about" element={<About />} />
    <Route path="/newsletter" element={<Newsletter />} />
    <Route
      path="/lamps"
      element={<ProductList products={lamps} type={"Lamps"} />}
    />
    <Route
      path="/candles"
      element={<ProductList products={candles} type={"Candles"} />}
    />
  </Routes>
</main>
```

## Making a Functional Navigation

- What's the difference between an anchor tag `a` and the link tags `Link, NavLink` provided by `react-router-dom`?
- What's the difference between `Link` and `NavLink`?
- Why do these components use `to` instead of `href`?

```js
import { Links, NavLink } from "react-router-dom";

export default function Header() {
  return (
    <header>
        <Link to="/">
            <h1>I Love Light</h1>
        </Link>

        <nav>
            <NavLink to="/about">About</NavLink>
            <NavLink to="/newsletter">Newsletter</NavLink>
            <NavLink to="/lamps">Lamps</NavLink>
            <NavLink to="/candles">Candles</NavLink>
        </nav>
    </header>
  );
}
```

## Make Views for Each Product

- How would you write out the link `/${type.toLowerCase()}/${product.id}` for each product?
- The React Router `useParams()` hook accesses route parameters, how could you determine which parameters are being returned from this function?
- What's the relationship between the link we built in the `ProductList` and the parameter we're extracting with `useParams()`?
- Some of the routes in the `App.js` use a new syntax that looks like this `:id`. What are we doing in these routes?

```js
import { Link, Route, Routes, useParams } from "react-router-dom";

// ProductList component
function ProductList({ products, type }) {
  return (
    <div>
      <h2>{type}</h2>
      <ul>
        {products.map((product) => (
          <li key={product.id}>
            <Link to={`/${type.toLowerCase()}/${product.id}`}>
              {product.name}
            </Link>
          </li>
        ))}
      </ul>
    </div>
  );
}

// Product component
function Product({ products, type }) {
  const { id } = useParams();
  const product = products.find((product) => product.id === id);

  return (
    <div>
      <h2>{type} Details</h2>
      {product ? (
        <div>
          <h3>{product.name}</h3>
          <p>{product.description}</p>
        </div>
      ) : (
        <p>Product not found.</p>
      )}
    </div>
  );
}

// App component
function App() {
  const lamps = [...]; // Array of lamp products
  const candles = [...]; // Array of candle products

  return (
    <div>
      <Routes>
        <Route
          path="/"
          element={<ProductList products={lamps} type="Lamps" />}
        />
        <Route
          path="/lamps/:id"
          element={<Product products={lamps} type="Lamps" />}
        />
        <Route
          path="/candles"
          element={<ProductList products={candles} type="Candles" />}
        />
        <Route
          path="/candles/:id"
          element={<Product products={candles} type="Candles" />}
        />
      </Routes>
    </div>
  );
}
```

## Change the view after an event

- What does "changing the view programmatically" mean?
- What is `useNavigate`?
- What types of events might you want to redirect the user after?

```js
// Using useNavigate for programmatic navigation
import { useNavigate } from "react-router-dom";

// Navigating to a different view on button click
const navigate = useNavigate();
const handleButtonClick = () => {
  navigate("/"); // Redirect to the home page
};
```

## Redirect to a New Page

- What is `Navigate`?
- What would be a good use case for `Navigate`?

```js
// Using the Navigate component for redirection
import { Navigate } from "react-router-dom";

// Inside a component or event handler
return <Navigate to="/about" />;
```