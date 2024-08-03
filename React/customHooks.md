## Custom Hooks

When you have a statful logic that is being repeated multiple times, you can use custom hooks to prevent that and reuse the hook whenever needed.✨

### Steps to Create Custom Hooks

1. **Identify the repeated code:**  
   Example: One of the common ones is _data fetching logic_.

2. **Create the Hook:**  
   Create a new file and name the file, and more importantly, the function starting with `use`.  
   Now you can program the logic for state management and side effects handling in this file.

3. **Return Values:**  
   Return the necassary values that you're going to use in your components.  
   Usually, you need to return the _states_ and the _functions_ that manipulate those states.

4. **Use Your Hook:**  
   Your hook is ready to be used to make your code more professional and easier to read and manage.🎉

### Example:

**_This is a custom hook for fetching data from an API._**

**`useFetch.jsx`**

```javascript
import { useState, useEffect } from "react";
import axios from "axios";

const useFetch = (url) => {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  const fetchData = async () => {
    try {
      const response = await axios.get(url);
      setData(response.data);
    } catch (err) {
      setError(err);
    } finally {
      setLoading(false);
    }
  };

  useEffect(() => {
    fetchData();
  }, [url]);

  return { data, loading, error };
};

export default useFetch;
```

_Notes for better understanding the code:_  
✅There are states defined using `useState`. These would be the states that we need to manage in another component without the custom hook.  
✅Then the `fetchData` function is defined which will handle the request. (`finally` will run after the `try` and `catch` blocks are finished.)  
✅Then `useEffect` is used to execute the `fetchData` function in the initial render and whenever the `url` is changed. ([About `useEffect` Hook](useEffect.md) )  
✅Finally, the states are returned by our custom hook. (There was no need to return the `fetchData` functin in this example. But we could return it.)

**_Now using the custom hook in other components:_**

**`MyComponent.jsx`**

```javascript
import React from "react";
import useFetch from "./useFetch";

const MyComponent = () => {
  const { data, loading, error } = useFetch("https://some-url.com");

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error.message}</p>;

  return (
    <div>
      <h1>Data</h1>
      <pre>{JSON.stringify(data, null, 2)}</pre>
    </div>
  );
};

export default MyComponent;
```

### A Note about _English_ language:

Don't mix these up.👀

- **Costume**:
  - noun meaning outfit, clothing
  - verb meaning dress someone in a particular set of clothes.
- **Custom**:
  - noun meaning tradition, convention
  - **adjective meaning made, like custom-made** 👈
