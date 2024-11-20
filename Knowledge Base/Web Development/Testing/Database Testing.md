# Database Testing

There is a limitation to this: we can't use real data in tests. This is because if there's a problem with a function, it can actually damage user data. Therefore, in order to perform tests, developers add random meaningless data to the database and then delete it.

So, the algorithm is as follows: add test data to the database → test → delete test data.

 Jest provides four methods that can help us with this:

-   `beforeAll()` and `afterAll()` will respectively run before and after running all tests in a file.
-   `beforeEach()` and `afterEach()` will run before and after each test, respectively. These will take longer and are more diligent, as they run twice for every test you write.

Say we want to run database tests using sample data. We can add it to the database before we run the tests and delete it after they are finished; the`beforeAll()` and `afterAll()` methods are perfect for this.

At the beginning of each test, we'll add test data to the database, and then we'll delete it at the end. This is where `beforeEach()` and `afterEach()` help us.

```jsx
beforeAll(() => {
  // connecting to the database
}); 

afterAll(() => {
  // disconnecting from the database
});

describe('Database tests', () => {

  beforeEach(() => {
    // before each test, add the needed test data to the database
  });

  afterEach(() => {
    // after each test, remove the data from the database
  });

  test('should test...', () => {/* code to check if the tests function properly */});
});
```

We can also call the `beforeAll()` and `afterAll()` methods inside the `describe()` block. Then, the `beforeAll()` and `afterAll()` callbacks will be called at the beginning and end of the test suite, respectively:

```jsx
beforeAll(() => {
  // connecting to the database
}); 

afterAll(() => {
  // disconnecting from the database
});

describe('Database tests', () => {
  beforeAll(() => { // will run before all tests inside this describe() block
    // code that adds the necessary test data before the tests run
  });

  afterAll(() => { // will run after all tests inside this describe() block
    // code that removes the test data from the database after all the the tests have run
  });

  test('db...', () => {/*  code to check db tests */});
  test('performs other tests...', () => {/* code to check other tests */});
});

describe('Endpoint tests', () => {
  /*
    beforeAll() and afterAll() from the previous describe() block
    won't be run here, but the global beforeAll() and afterAll() will be run
  */

    test('the endpoints', () => {/* code to check tests */});
})
```

The `beforeAll()`, `afterAll()`, `beforeEach()`, and `afterEach()` methods let us test our databases "silently", that is, we add test data and then simply erase it after we're finished. The important thing is that we carefully arrange all our testing methods, and this skill comes with practice.