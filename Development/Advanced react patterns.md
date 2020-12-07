# Learnings taken from: [kentcdodds/advanced-react-patterns](https://github.com/kentcdodds/advanced-react-patterns)

## Exercise 1
When creating **contexts** , we can create helpers that accept `dispatch`. It solves the annoyances, avoiding the use of: `useCallback`.
This pattern reduce duplication, and also helps improve performance.

**Example**
```javascript
function useCounter() {
  const context = React.useContext(CounterContext);

  return context;
}

const increment = dispatch => dispatch({type: 'increment'})
const decrement = dispatch => dispatch({type: 'decrement'})

export {CounterProvider, useCounter, increment, decrement}
```

## Exercise 2
Compound components are components that work together to form a complete UI. You can share the state by providing the compound components with the props they need implicitly, using: `Children` e `cloneElement`.

**Example**
```javascript
function Toggle({ children }) {
  const [on, setOn] = React.useState(false);

  const toggle = () => setOn(oldOn => !oldOn);

  return React.Children.map(children, child => {
    return child.type === 'string'
      ? child
      : React.cloneElement(child, { on, toggle });
  });
}
```

## Exercise 3
A better way to keep flexible the compound components, is through: `createContext`.

## Exercise 4
You can give rendering control to users, returning a object of props from your component, or maybe a function that override them. This make it easier to use your components and hooks the right way without requiring people to wire things up for common use cases.

## Exercise 5
We can override reducer logic  in many different contexts, and scenarios providing a custom reducer as prop.