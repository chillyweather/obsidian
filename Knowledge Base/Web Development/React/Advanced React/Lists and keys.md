# Lists and Keys

Исходные данные
```json
const chats = [{
  id: 10,
  name: 'Gregory',
  lastMessageAt: '20:45',
}, {
  id: 5,
  name: 'Allison',
  lastMessageAt: '12:31',
}, {
  id: 3,
  name: 'James',
  lastMessageAt: '07:40',
}];
```

Рендер списка чатов
```jsx
ReactDOM.render((
  <>
    <h2>Chats</h2>
    {chats.map((chat) => (
      <Chat id={chat.id} name={chat.name} lastMessageAt={chat.lastMessageAt} />
    ))}
  </>
), document.querySelector('#root'));
```

Собственно элемент чата
```jsx
function Chat(props) {
  return (
    <div className="chat">
      <img src={`img/${props.id}.png`} width="75" />
      <h2>{props.name}</h2>
      <div className="date">{props.lastMessageAt}</div>
    </div>
  );
}
```


To help the algorithm understand that the order of elements has changed we'll use a special `key` attribute. The `key` is a unique identifier for the node, and is used as the third criterion in the comparison. React will compare new chat lists using this attribute to see if the elements have changed their order within the list.

```jsx
ReactDOM.render((
  <>
    <h2>Chats</h2>
    {chats.map((chat) => (
      <Chat
                key={chat.id}
                id={chat.id}
                name={chat.name}
                lastMessageAt={chat.lastMessageAt}
            />
    ))}
  </>
), document.querySelector('#root'));
```

### Keys Outside Lists
`key` can be used for more than just lists. For example, after selecting a chat, it may be necessary to replace the entire message list for which the `MessageList` component is responsible.

Sometimes, the easiest solution is to "ask" React to completely unmount the old `MessageList` component and to mount a new one in its place. This can be done by assigning the component a new `key` that corresponds to the selected chat `id`:
```jsx
ReactDOM.render((
  <>
    <h2>Chats</h2>
    {chats.map((chat) => (
      <Chat
                key={chat.id}
                id={chat.id}
                name={chat.name}
                lastMessageAt={chat.lastMessageAt}
            />
    ))}

        <h2>Messages</h2>
        <MessageList key={selectedChatId} />
  </>
), document.querySelector('#root'));
```

By changing the `key`, we're telling React that the current instance of the `MessageList` component must be completely replaced with a new instance.