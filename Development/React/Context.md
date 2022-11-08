
We can share information between components with contexts.

## How to use a React Context

1. Create a context with the react function **createContext**
2. Create a component that will be the provider. For example `UserProvider.jsx` This is going to receive the **children** components on the props and return a Provider from the context created at step 1.
3. Use the context on any component that is a child of the provider by using the **useContext** hook.