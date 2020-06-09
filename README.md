# debounce-and-throttling
Debouncing and throttling techniques are used to limit the number of times a function can execute.

```js
// It will expect a certain time delay to execute the callback function.
const debounce = (func, delay) => {
  let inDebounce;
  return function() {
    const context = this;
    const args = arguments;
    clearTimeout(inDebounce)
    inDebounce = setTimeout(() => func.apply(context, args), delay)
  }
}
```
----
```js
// It will wait a certain time limit to make the next callback function execution.
const throttle = (func, limit) => {
  let inThrottle;
  return function() {
    const args = arguments;
    const context = this;
    if (!inThrottle) {
      func.apply(context, args)
      inThrottle = true;
      setTimeout(() => inThrottle = false, limit)
    }
  }
}
```
