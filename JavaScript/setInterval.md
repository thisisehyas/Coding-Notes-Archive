## setInterval() function

`setInterval()` is a built-in function that you can use to make a certain function run repeatedly at each time interval that you define.

### Syntax:
```javascript
const timer = setInterval(() => {
    // code to run repeatedly
}, milliSecond);
```

### Example:
```javascript
const timer = setInterval(() => {
    console.log('This message will be logged every second');
}, 1000);
```

**Note:**
Always clear the interval after usage. (Unless the logic requires you not to.)
You can clear the interval using:
`clearInterval(timer);`

This stops the repeated execution of the function.

### Example of Clearing the Interval:
In the previous example you could clear the interval like this:
```javascript
const timer = setInterval(() => {
    console.log('This message will be logged every second');
}, 1000);

// Clear the interval after some condition or timeout
clearInterval(timer);
```