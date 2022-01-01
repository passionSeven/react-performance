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

### How to make Lazy loading more Eager?

- loading when the user hovers over
  - onMouseEnter
  - onFocus (keyboard!)

#### [`onMouseEnter` vs `onMouseOver`](https://stackoverflow.com/questions/1638877/difference-between-onmouseover-and-onmouseenter)

- `enter` doesn't fire again (bubble) when going into a child element
