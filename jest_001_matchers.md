# Jest Matchers

https://jestjs.io/docs/using-matchers

## Equality Matchers

### .toBe()
```js
expect(2 + 2).toBe(4);
```

### .toEqual()

Used for checking equality with objects/arrays
```js
expect({one: 1, two: 2}).toEqual({one: 1, two: 2});
```

### .not()

Check not equal

```js
expect(2).not.toBe(0);
```

## Truthiness

- `.toBeNull()` matches only null
- `.toBeUndefined()` matches only undefined
- `.toBeDefined()` is the opposite of toBeUndefined
- `.toBeTruthy()` matches anything that an if statement treats as true
- `.toBeFalsy()` matches anything that an if statement treats as false

## Numbers

```js
expect(value).toBeGreaterThan(3);
expect(value).toBeGreaterThanOrEqual(3.5);
expect(value).toBeLessThan(5);
expect(value).toBeLessThanOrEqual(4.5);

// toBe and toEqual are equivalent for numbers
expect(value).toBe(4);
expect(value).toEqual(4);
```

> For **floating point** equality, use `.toBeCloseTo()` instead of `.toEqual()`, because you don't want a test to depend on a tiny rounding error

## Strings

You can check strings against regular expressions with `.toMatch()`

```js
expect('team').not.toMatch(/I/);
expect('Christoph').toMatch(/stop/);
```

## Arrays and Iteratables

You can check if an array or iterable contains a particular item using `.toContain()`

```js
const shoppingList = [
  'diapers',
  'kleenex',
  'trash bags',
  'paper towels',
  'milk',
];

test('the shopping list has milk on it', () => {
  expect(shoppingList).toContain('milk');
  expect(new Set(shoppingList)).toContain('milk');
});
```

## Exceptions

If you want to test whether a particular function throws an error when it's called, use `.toThrow()`

```js
function compileAndroidCode() {
  throw new Error('you are using the wrong JDK!');
}

test('compiling android goes as expected', () => {
  expect(() => compileAndroidCode()).toThrow();
  expect(() => compileAndroidCode()).toThrow(Error);

  // You can also use a string that must be contained in the error message or a regexp
  expect(() => compileAndroidCode()).toThrow('you are using the wrong JDK');
  expect(() => compileAndroidCode()).toThrow(/JDK/);

  // Or you can match an exact error message using a regexp like below
  expect(() => compileAndroidCode()).toThrow(/^you are using the wrong JDK$/); // Test fails
  expect(() => compileAndroidCode()).toThrow(/^you are using the wrong JDK!$/); // Test pass
});
```

> The function that throws an exception needs to be invoked within a wrapping function otherwise the `.toThrow()` assertion will fail.