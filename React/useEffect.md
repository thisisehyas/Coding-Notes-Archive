## `useEffect` Hook

#### `useEffect` Hook LifeCycle (when there exists a dependency array)

- **Initial Render:**  
  When the component first renders, the `useEffect` hook runs regardless of what's in the dependency array.

- **Subsequent Renders:**  
  After the initial render, the `useEffect` hook will only run again if one or more values in the dependency array change.

### Three Case Scenarios:

1. **The code below runs only once, after the initial render.**  
   (Note the empty dependency array.)
    ```javascript
    useEffect(() => {
        // Code here runs once after initial render
    }, []);
    ```

2. **The code below runs after every render, including the initial render.**  
   (Note that there's no dependency array.)
    ```javascript
    useEffect(() => {
        // Code here runs after every render
    });
    ```

3. **The code below runs after the initial render and whenever `countdown` or `showVerification` changes.**
    ```javascript
    useEffect(() => {
        // Code here runs after initial render and whenever
        // `countdown` or `showVerification` changes
    }, [countdown, showVerification]);
    ```


