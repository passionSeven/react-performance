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

### Webpack magic comments (prefetching)

- [Webpack magic comments docs](https://webpack.js.org/api/module-methods/#magic-comments)

```js
import(/* webpackPrefetch: true */ './some-module.js')
```

- adds `rel="prefetch"` and `as="script"`

```html
<link rel="prefetch" as="script" href="/static/js/1.chunk.js" />
```

- `webpackChunkName`: put common modules together in the same chunk
  - less of an optimization now that we have multiplexing in HTTP2+

#### Does vite and snowpack have this too?

## useMemo

```jsx
const distance = React.useMemo(() => calculateDistance(x, y), [x, y])
```

- for memoizing values

## React.useMemo

- only re-renders when the props change
- accepts a `comparator(prevProps, newProps)`
   - return `true`: memoize
   - `false`: don't memoize (aka re-render)
   - avoid premature optimization!
     - makes the code way more complex
- React will memoize for us if we pass only primitives as props
