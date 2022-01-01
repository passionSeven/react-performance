## Code Splitting

- import() is promisable

```js
import('/some-module.js').then(
```

- React.lazy() loads the default export

```jsx
const SmileyFace = React.lazy(() => import('./smiley-face'))
```

- [here's how to lazily load a default export](https://stackoverflow.com/a/66289130/8479344)

```jsx
const FontAwesomeIcon = React.lazy(() =>
  import('@fortawesome/react-fontawesome').then(module => ({
    default: module.FontAwesomeIcon,
  })),
)
```
