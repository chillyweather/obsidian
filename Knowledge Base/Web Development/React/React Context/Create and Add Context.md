# Create and Add Context

A context is usually created in a separate file and then exported from it. Sometimes, this file may also contain and export a few extra options which are stored inside an object.

```jsx
// translationContext.js

export const TranslationContext = React.createContext();

export const translations = {
  en: {
    greeting: 'Hello World',
  },
  ru: {
    greeting: 'Привет, мир!',
  },
};
```

`Provider` component has a prop called `value`. We'll pass the values here that will be assigned to all the children:

```jsx
// App.js

// import the context object
import { TranslationContext, translations } from './translationContext';

function App() {
  // state responsible for the current language
  const [lang, setLang] = React.useState('en');

  return (
        // Use data from translations[lang] using Context.Provider
    <TranslationContext.Provider value={translations[lang]}>
            {/* The subtree, in which the context will be accessed */}  
      <Main />
    </TranslationContext.Provider>
  );
}
```

In the example above, we're passing in the value of `translation[lang]` (in our case it's 'Hello World') to the `Provider` component's `value` property. Not only that, this value is dynamic. We can switch to a different language setting based on the value of `lang`, which will select the corresponding property on the `translations` object.

Even though the `Provider` component automatically passes our context through the component tree, we'll still need to manually connect each individual child component that will actually use the data.