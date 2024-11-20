# Subscribe to a Context

- in functional component
```jsx
function Header() {
  // subscribing to TranslationContext
  const translation = React.useContext(TranslationContext);

  // printing the contents of translations.en.greeting,
  // which is now available through translation.greeting
  return (
    <h1>
      {translation.greeting}
    </h1>
  );
}
```

- in class component
```jsx
import { TranslationContext } from './translationContext';

class Header extends React.Component {
  static contextType = TranslationContext;

    // printing the contents of translations.en.greeting,
  // which is now available through this.context.greeting
  render() {
    return (
      <h1>
        {this.context.greeting}!
      </h1>
    );
  }
}
```

## Use multiply providers
```jsx
/* Importing the context objects */
import { TranslationContext, translations } from './translationContext';
import { CurrentUserContext } from './currentUserContext';

function App() {
  // state responsible for the current language
  const [lang, setLang] = React.useState('en');

  // state responsible for the data of the current user
  const [currentUser, setCurrentUser] = React.useState({ name: 'David' });

  return (
    // embedding data from translations[lang] using the first context provider
    <TranslationContext.Provider value={translations[lang]}>
      {/* embedding data from the currentUser using the second context provider */}
      <CurrentUserContext.Provider value={currentUser}>
        {/* subtree in which both contexts will be available */}
        <Main />
      </CurrentUserContext.Provider>
    </TranslationContext.Provider>
  );
}
```