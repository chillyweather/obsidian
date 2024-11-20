# Functional components in React

```jsx
// a component named User
function User(props) {
  return (
    <p>
      <img src={`https://code.s3.yandex.net/web-code/react/${props.id}.png`} width="75" />
      <br />
      <b>{props.name}</b>
    </p>
  );
}

// the main app code
ReactDOM.render((
  <>
    <h2>My imaginary friends:</h2>
    <User id="1" name="Gregory" />
    <User id="2" name="James" />
    <User id="3" name="Allison" />
  </>
), document.querySelector('#root'));
```

```jsx
function Animal(props) {
  // get the current time in hours
  const hours = new Date().getHours();
  // check if it's night
  const isNight = hours > 19 || hours < 6;
  // depending on the time of day, different animals should be asleep or awake
  const isSleeping = (isNight && !props.isNocturnal) || (!isNight && props.isNocturnal);

  return (
    <div className="animal">
      <div className="icon">{isSleeping ? "💤" : props.icon}</div>
      <div className="info">
        <h3>{props.name}</h3>
        <span>{props.height}</span>
      </div>
    </div>
  );
}

ReactDOM.render((
  <>
    <h2>Africa</h2>
    <Animal icon="🦒" name="Giraffe" height="17 feet" isNocturnal={false} />
    <Animal icon="🦔" name="Hedgehog" height="6 inches" isNocturnal={true} />
    <Animal icon="🦨" name="Skunk" height="Too smelly to measure" isNocturnal={true} />
  </>
), document.querySelector('#root'));
```