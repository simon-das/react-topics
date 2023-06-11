# Internationalization (i18n)
Internationalization, often abbreviated as i18n, is the process of designing and adapting an application to support multiple languages and locales. It involves translating text, 
formatting numbers and dates, and handling other cultural differences.

Internationalization can be achieved using libraries such as react-intl. The react-intl can be used for internationalization in the following way:

1. Install react-intl: `npm install react-intl`

2. Import the necessary components and hooks from react-intl:
```javascript
import { IntlProvider, FormattedMessage, useIntl } from 'react-intl';
```

3. Wrap your application or a specific part of it with the `IntlProvider` component and provide the necessary configuration:
```javascript
<IntlProvider locale="en" messages={messages}>
  {/* Your application components */}
</IntlProvider>
```
In this example, we're setting the locale to "en" (English) and providing the `messages` object containing the translations for the English language.

4. Define the translation messages for different languages:
```javascript
const messages = {
  en: {
    greeting: 'Hello, {name}!',
  },
  fr: {
    greeting: 'Bonjour, {name} !',
  },
};
```
Here, we have defined the translation messages for English and French languages.

5. Use the `FormattedMessage` component to display the translated text in your application:
```javascript
<FormattedMessage
  id="greeting"
  defaultMessage="Hello, {name}!"
  values={{ name: 'John' }}
/>
```
The `id` property represents the translation key, the `defaultMessage` is the fallback message if the translation is not available, and the `values` object provides any dynamic values to be substituted in the translated message.

<br>

Additionally, you can use the `useIntl` hook to access the `formatMessage` function for programmatic translation within your components. 
The API should be utilized in cases where a React element is not appropriate, such as when setting a title or aria attribute, or when performing a side effect in the componentDidMount lifecycle method.
```javascript
import { useIntl } from 'react-intl';

function MyComponent() {
  const intl = useIntl();
  const translatedMessage = intl.formatMessage({ id: 'greeting', defaultMessage: 'Hello, {name}!', values: { name: 'John' } });

  return <div>{translatedMessage}</div>;
}
```

<br>

## Reference
https://formatjs.io/docs/react-intl#formatting-data
