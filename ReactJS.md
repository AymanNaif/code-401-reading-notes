# React Notes

## Lifting State Up
- To lift state up from a child component to a parent component:
	1. Define a function in the parent component to receive the value.
		- Example: 
		```javascript
		const getData = (enteredData) => {
			const data = enteredData;
		}
		```
	2. Pass this function as a prop to the child component.
		- Example: `<ChildComponent savedData={getData} />`
	3. Call the function inside the child component using the prop.
		- Example: `props.savedData(theDataPassed)`

## Portal
- Portals are used to render a component at a different place in the DOM.

## Hooks
- `useRef()`: 
	- Used to access or store references to DOM elements or other mutable values without triggering a re-render.
	- Example: `<input ref={inputRef} type="text" />`
- `useEffect()`: 
	- Allows performing side effects in functional components, such as fetching data, subscribing to events, or manipulating the DOM.
	- Example: 
		```javascript
		useEffect(() => {
			// Side effect code here
			
			return () => {
				// Cleanup code here
			};
		}, [dependencies]);
		```
- `useReducer()`: 
	- Used for managing complex state logic in functional components.
	- Provides a powerful alternative to `useState` when handling state transitions involving multiple actions and complex updates.
- `useContext()`: 
	- Used to share data between components without passing it through every level of the component tree.
	- Example:
		1. Create a context: `const MyContext = createContext();`
		2. Create a provider component: 
			```javascript
			function MyProvider({ children }) {
				const value = 'Hello, World!';
				return <MyContext.Provider value={value}>{children}</MyContext.Provider>;
			}
			```
		3. Wrap the component that needs access to the data with the provider.
		4. Use `useContext` to access the value.
			```javascript
			const value = useContext(MyContext);
			```
- `React.memo()`: 
	- A higher-order component used to memoize the rendering of a functional component.
	- Optimizes rendering performance by preventing unnecessary re-renders.

- `useCallback()`: 
	- Stores a function across component executions to prevent re-creation on every re-render.
	- Useful when you want to memoize a function and re-create it only when the dependencies change.

- `useMemo()`: 
	- Stores data (e.g., arrays, objects) instead of a function.
	- Used for memoizing expensive calculations to avoid recalculating the data.

## Custom Hooks
- Functions that use stateful logic for managing state.
- Start with the prefix "use".
- Created to encapsulate common state logic for reusability.

## Redux
- Redux is a state management library.
- Communication between the store and reducer is established, and the store is subscribed to a subscriber function.
	1. Create a reducer function.
	2. Create a store using `createStore` with the reducer.
	3. Subscribe to the store using a subscriber function.
	4. For React projects, use `react-redux`:
		- Import `Provider` from `react-redux` in the top level of the application (usually in `index.js`).
		- Wrap the app with the `Provider` component and pass the store as a prop.
		- Use `useSelector` to access values from the store in a component.
		- Use `useDispatch` to dispatch actions.

## Redux Toolkit
- Redux Toolkit simplifies the usage of Redux.
- Steps:
	1. Import `createSlice` and `configureStore` from `@reduxjs/toolkit`.
	2. Use `createSlice` to define an object with `name`, `initialState`, and `reducers`.
	3. Use `configureStore` with the reducer to create the store.
	4. Export the store and actions.
	5. Inside the component, use `useSelector` to access the state and `useDispatch` to dispatch actions.

## React Routing
- Routing is used to navigate between different pages in a React application.
	1. Install the `react-router-dom` package.
	2. Use `createBrowserRouter` or `createRouteFromElements` to define the routes.
	3. Wrap the app with `RouterProvider` and provide the router.
	4. Use `Link` or `NavLink` to navigate between pages.
	5. Use `useNavigate` to navigate programmatically.

## Concepts and Terms
- Two-way binding
- Controlled and uncontrolled components
- Styled components (CSS styling with a package)
- Debouncing
- Cleanup function for `useEffect`
