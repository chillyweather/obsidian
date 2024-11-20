# Working with forms

**Controlled components** - elements used to control forms, whose value are synchronized with the state of the component in which they're located. This is convenient because it allows us to directly manipulate the content of forms with JavaScript.

Let's see an example of a controlled component:
```jsx
function Input() {
  // state containing the value of the input
  const [value, setValue] = React.useState('');

  // the input event handler changes the state  
  function handleChange(e) {
    setValue(e.target.value);
  }

  return (
    // the value of the element is bound to the state value
    <input type="text" value={value} onChange={handleChange} />
  );
}

ReactDOM.render((
  <Input />
), document.querySelector('#root'));
```

Add display and reset buttons
```jsx
function Input() {
  const [value, setValue] = React.useState('');

  function handleChange(e) {
    setValue(e.target.value);
  }

  function handleDisplay() {
    alert(value);
  }

  function handleReset() {
    setValue('');
  }

  return (
    <>
      <input type="text" value={value} onChange={handleChange} />
      <button onClick={handleDisplay}>Display</button>
      <button onClick={handleReset}>Reset</button>
    </>
  );
}
```