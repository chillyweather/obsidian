# Testing Frameworks and Methods

```bash
npm install --save-dev jest
```

```jsx
// package.json
...
"scripts": {
  "test": "jest"
},
...
```

### How to Write Tests

Now, we can start creating a test for the greeting function. In Jest, the `test()` function or its alias `it()` are used for this. Either one will work — they're interchangeable. The first parameter is the name of the test, the second parameter is the function to be run.

```jsx
test('What the function under test should do', () => {
  // expected output depending on the input
});

it('What the function under test should do', () => {
  // expected output depending on the input
});
```

The `expect()` function comes in handy here. It takes the expected value as an argument and returns an object with methods for testing, which are referred to as matcher functions. One of these matcher functions is the `toBe()` method, which compares its own argument to the one passed to the `expect()` function:

```jsx
expect(1).toBe(1); // true
expect(1).toBe(2); // false
expect(1 + 2).toBe(3); // true
```

So, we can pass the result of the `sayHello()` function to the `expect()` function and compare it with the expected output like so:

```jsx
test('Creates a greeting', () => {
    expect(sayHello('Lera', 'Jackson')).toBe('Hello, Lera Jackson!');
});
```

### Primary Testing Methods

- `toBe()` is used to compare primitive values and object references
- `toEqual()` is used to compare objects and arrays. When comparing objects, this method checks that the resulting object contains all the same keys with the same values as the expected one. If the object being tested contains any properties that are not specified in the expected object, the `toEqual()` method will simply ignore them. When comparing arrays, the `toEqual()` method checks that all the items in the real output are exactly the same as in the expected output. This said, missing elements and `undefined` are considered equal:

```jsx
  // tests will pass
  expect({ a: undefined, b: 10, c: 'text' }).toEqual({ b: 10, c: 'text' });
  expect([1, 2, 3]).toEqual([1, 2, 3]); 
  expect([[undefined, 1]]).toEqual([[, 1]]) // the first element is missing in the second array

  // tests won't pass
  expect({ a: undefined, b: 10, c: 'text' }).toEqual({ a: 12, b: 10, c: 'text' });
  expect([1, 2, 3, undefined]).toEqual([1, 2, 3]); // arrays do not match in length
  
```

- `toStrictEqual()` is also used to compare objects and arrays, but "more strictly." The output object (array) must match the expected one exactly. In other words, it must have all the same properties (items). In the following example, `undefined` and the missing element are not equivalent:

```jsx
  // tests will pass
  expect({ b: 10, c: 'text' }).toStrictEqual({ b: 10, c: 'text' });
  expect([3, 4, undefined]).toStrictEqual([3, 4, undefined]);

  // tests won't pass
  expect({ a: undefined, b: 10, c: 'text' }).toStrictEqual({ b: 10, c: 'text' });
  expect([[undefined,  1]]).toStrictEqual([[, 1]])
  
```

- `toBeTruthy()` and `toBeFalsy()` check that the output is `true` or `false`, respectively:

```jsx
  // tests will pass
  expect(1).toBeTruthy();
  expect(true).toBeTruthy();
  expect(undefined).toBeFalsy();
  expect(1/'string').toBeFalsy();

  // tests won't pass
  expect(null).toBeTruthy();
  expect(0).toBeTruthy();
  expect(true).toBeFalsy();
  
```

- `toBeUndefined()` and `toBeDefined()` compare the output with `undefined`.

The first method, `toBeUndefined()`, checks if the output is `undefined`.

The second one, `toBeDefined()`, does the opposite, i.e. it checks that the result is not `undefined`. This test will pass even with the value of `null`, which is considered defined.

```jsx
  // tests will pass
  expect(1).toBeDefined();
  expect(null).toBeDefined();
  expect('string').toBeDefined();

  // tests won't pass
  const x;

  expect(x).toBeDefined();
  expect(undefined).toBeDefined();
  
```

- `toBeNull()` checks that the output is `null`
- `toMatch()` checks whether a string matches a regular expression:
```jsx
  // tests will pass
  expect('1').toMatch(/^\d+$/);
  expect('1337').toMatch(/^\d+$/);
  expect('4242').toMatch(/^\d+$/);

  // tests won't pass
  expect('21as1').toMatch(/^\d+$/);
  expect('string').toMatch(/^\d+$/);
  
```

- `toContain()` checks whether the resulting array contains the value we specify. It works with strings too:
```jsx
  // these tests will pass
  expect('Oh, hi Mark!').toContain('Mark');
  expect(['Mary', 'Louisa', 'Stuart']).toContain('Stuart');

  // these tests won't pass
  expect('Oh, hi Mark!').toContain('Lisa');
  expect(['Mary', 'Louisa', 'Stuart']).toContain('Louise');
  
```

- `toBeGreaterThan()`, `toBeGreaterThanOrEqual()`, `toBeLessThan()`, and `toBeLessThanOrEqual()`

## Full list of methods:
https://jestjs.io/docs/expect