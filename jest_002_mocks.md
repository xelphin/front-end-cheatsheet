# Jest Mocks

```js
const Sample = (function Sample() {
    
    const forEach = (items, callback) => {
        for (let index = 0; index < items.length; index++) {
            callback(items[index]);
          }
    }

    return {
        forEach
    };
})();

export default Sample;
```

We can use a `Mock` to check that forEach() works

```js
import Sample from "./sample";

const mockCallback = jest.fn(x => 42 + x);

test('forEach mock function', () => {
    Sample.forEach([0, 1], mockCallback);

  // The mock function ('mockCallback()') was called twice
  expect(mockCallback.mock.calls).toHaveLength(2);

  // The first argument of the first call to the function was 0
  expect(mockCallback.mock.calls[0][0]).toBe(0);

  // The first argument of the second call to the function was 1
  expect(mockCallback.mock.calls[1][0]).toBe(1);

  // The return value of the first call to the function was 42
  expect(mockCallback.mock.results[0].value).toBe(42);
});
```

## More Info

```js
// const fn = jest.fn()
// const fn = jest.fn().mockName('Unicorn') -- named mock, Jest 22+
expect(fn).toBeCalled() // Function was called
expect(fn).not.toBeCalled() // Function was *not* called
expect(fn).toHaveBeenCalledTimes(1) // Function was called only once
expect(fn).toBeCalledWith(arg1, arg2) // Any of calls was with these arguments
expect(fn).toHaveBeenLastCalledWith(arg1, arg2) // Last call was with these arguments
expect(fn).toHaveBeenNthCalledWith(callNumber, args) // Nth call was with these arguments (Jest 23+)
expect(fn).toHaveReturnedTimes(2) // Function was returned without throwing an error (Jest 23+)
expect(fn).toHaveReturnedWith(value) // Function returned a value (Jest 23+)
expect(fn).toHaveLastReturnedWith(value) // Last function call returned a value (Jest 23+)
expect(fn).toHaveNthReturnedWith(value) // Nth function call returned a value (Jest 23+)
expect(fn.mock.calls).toEqual([
  ['first', 'call', 'args'],
  ['second', 'call', 'args'],
]) // Multiple calls
expect(fn.mock.calls[0][0]).toBe(2) // fn.mock.calls[0][0] — the first argument of the first cal
```