# React CRUD

| Term | Definition |
| ---- | ---------- |
| __Resource__ |  A conceptual representation of data that has a set of properties with different potential values. Typically, resources are also something you want to save or store. |
| __API__ | A set of rules and protocols that allows different software applications to communicate with each other. |
| __CRUD__ | An acronym that stands for Create, Read, Update, and Delete. It represents the basic operations that can be performed on a resource. |
| __HTTP&nbsp;Requests__ | Requests made to a server using HTTP methods (GET, POST, PUT, DELETE) to perform CRUD operations. |
| __Index Page__ | A common page type that displays a list or collection of resources. |
| __Show Page__ | A common page type that shows detailed information about a specific resource. |
| __Edit Page__ | A common page type that allows users to modify the details of a specific resource. |
| __New Page__ | A common page type that provides a form or interface for creating a new resource. |
| __Axios__ | A popular JavaScript library that provides an easy-to-use API for performing asynchronous operations such as sending HTTP requests and handling responses. |

---

## GET Request with Fetch

- What's the purpose of the GET request?
- What does this code do with a successful response?
- What does this code do with an unsuccessful response?

```js
import React, { useEffect, useState } from 'react';

function MyComponent() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('/api/data')
      .then(response => response.json())
      .then(data => setData(data))
      .catch(error => console.error(error));
  }, []);

  //...
}
```

## GET Request with Axios

- What differences are there between the fetch call and the axios call?

```js
import React, { useEffect, useState } from 'react';
import axios from 'axios';

function MyComponent() {
  const [data, setData] = useState(null);

  useEffect(() => {
    axios.get('/api/data')
      .then(response => setData(response.data))
      .catch(error => console.error(error));
  }, []);

  // ...
}
```

## POST Request with Fetch

- What's the purpose of the POST request?
- Why do we run the POST request on form submit?

```js
import React, { useState } from 'react';

function MyComponent() {
  const [newData, setNewData] = useState('');

  const handleSubmit = () => {
    fetch('/api/data', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({ data: newData }),
    })
      .then(response => response.json())
      .then(data => console.log(data))
      .catch(error => console.error(error));
  };

  // ...
}
```

## POST Request with Axios

- What differences are there between the fetch call and the axios call?

```js
import React, { useState } from 'react';
import axios from 'axios';

function MyComponent() {
  const [newData, setNewData] = useState('');

  const handleSubmit = () => {
    axios.post('/api/data', { data: newData })
      .then(response => console.log(response.data))
      .catch(error => console.error(error));
  };

  // ...
}
```

## PUT Request with Fetch

- What's the purpose of the PUT request?
- What data would likely be dynamic in a real world application?
- What's a common way we can allow the user to update data?

```js
import React, { useState } from 'react';

function MyComponent() {
  const [data, setData] = useState('');

  const handleUpdate = () => {
    fetch('/api/data/123', {
      method: 'PUT',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({ updatedData: data }),
    })
      .then(response => response.json())
      .then(data => console.log(data))
      .catch(error => console.error(error));
  };

  // ...
}
```

## PUT Request with Axios

- What differences are there between the fetch call and the axios call?

```js
import React, { useState } from 'react';
import axios from 'axios';

function MyComponent() {
  const [data, setData] = useState('');

  const handleUpdate = () => {
    axios.put('/api/data/123', { updatedData: data })
      .then(response => console.log(response.data))
      .catch(error => console.error(error));
  };

  // ...
}
```

## DELETE Request with Fetch

- What's the purpose of the DELETE request?
- What data would likely be dynamic in a real world application?
- What's a common interface update you might make after something has been deleted?

```js
import React, { useState } from 'react';

function MyComponent() {
  const handleDelete = () => {
    fetch('/api/data/123', {
      method: 'DELETE',
    })
      .then(response => console.log('Resource deleted successfully'))
      .catch(error => console.error(error));
  };

  // ...
}
```

## DELETE Request with Axios

- What differences are there between the fetch call and the axios call?

```js
import React from 'react';
import axios from 'axios';

function MyComponent() {
  const handleDelete = () => {
    axios.delete('/api/data/123')
      .then(() => console.log('Resource deleted successfully'))
      .catch(error => console.error(error));
  };

  // ...
}
```