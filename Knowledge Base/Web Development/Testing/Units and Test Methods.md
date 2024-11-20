# Units and Test Methods

### Which Functions Should Be Tested?

Ideally, all of them. To do this, we need to break our program down into units. A unit is the smallest part of code that can be tested in isolation. In our case, this essentially means any function.

```jsx
// check that the password contains a number
function checkNumber(pass) {
  if (typeof pass === 'string') {
    let regex = /\d/;
    return regex.test(pass); // the regex.test() method will return true if the passed string matches the regexp

    }
}

// check that the password contains a special character
function checkSymbol(pass) {
  if (typeof pass === 'string') {
    let regex = /[!@#$%^&*(),.?":{}|<>_]/;
    return regex.test(pass);
  }
}

// run both checks
function checkPass(pass) {
  return checkNumber(pass) && checkSymbol(pass);
}
```

```jsx
test('Check that the password contains a number', () => {
    expect(checkNumber('some_not_so_strong_pass')).toBe(false);
    expect(checkNumber('stronger_pass_123')).toBe(true);
});

test('Check that the password contains a special character', () => {
    expect(checkSymbol('somePass')).toBe(false);
    expect(checkSymbol('another_pass')).toBe(true);
});

test('Check password', () => {
    expect(checkPass('somePas$')).toBe(false);
    expect(checkPass('another_pass_123')).toBe(true);
});
```

