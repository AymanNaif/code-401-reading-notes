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
	- The primary use case for useRef is to access or store references to DOM elements or other mutable values without triggering a re-render. Unlike useState, updating the value stored in a useRef does not 	
	cause the component to re-render.(usually used for input field)
	- Example: `<input ref={inputRef} type="text" />`
- `useEffect()`: 
	-  This hook allows you to perform side effects in functional components, such as fetching data,
 subscribing to events, or manipulating the DOM. It takes a function as its first parameter, which will be executed after every render. You can also provide a cleanup function that will be executed before the 	component is unmounted.
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
	- The useReducer hook is another built-in hook provided by React. It is used for managing complex state 	logic in functional components. While the useState hook is suitable for managing simple state, 
	the useReducer hook provides a more powerful alternative when you need to handle state transitions 	that involve multiple actions and complex state updates.
	The useReducer hook follows the concept of a reducer function, which is a pure function that takes the 	current state and an action as arguments, and returns the new state based on the action. The reducer 	function specifies how state transitions should happen in response to different actions.
	The useReducer hook is another built-in hook provided by React. It is used for managing complex state 	logic in functional components. While the useState hook is suitable for managing simple state, 
	the useReducer hook provides a more powerful alternative when you need to handle state transitions 
	that involve multiple actions and complex state updates.
	The useReducer hook follows the concept of a reducer function, which is a pure function that takes the 	current state and an action as arguments, and returns the new state based on the action. The reducer 	function specifies how state transitions should happen in response to different actions. For ex check 
	chatGPT
- `useContext()`: 
	- Context provides a way to share data between components without explicitly passing it through 
		every level of the component tree. It is useful when you have data that needs to be accessed by 
		multiple components at different levels.
	- to apply that:
		1. Create a context: `const MyContext = createContext();`
		2. Create a provider component create a provider component  and export it
			```javascript
			function MyProvider({ children }) {
				const value = 'Hello, World!';
				return <MyContext.Provider value={value}>{children}</MyContext.Provider>;
			}
			```
		3. wrap the component you need to provide it with a data with the provider
		4. Use `useContext` to access the value.
			```javascript
			const value = useContext(MyContext);
			```
		5. use the value of it :D
- `React.memo(component)`: 
	- is a higher-order component (HOC) used to memoize the rendering of a functional component.
	- it is typically used to optimize the rendering performance of a functional component by preventing unnecessary re-renders.
	- It takes a component as an argument and returns a new memoized component.
	- The memoized component will only re-render if its props have changed.

- `useCallback()`: 
	- hook is used to store a function across component execution (save a function) to prevent 
		re-creation on every component re-render — so one function is create and store on a memory
		it take a dependancies such as useEffect and re-create it when dependancies is changed
		- Example: 
		```javascript
		useCallback(()=>, [dependancies])
		```

- `useMemo()`: 
	- is a hook such as  useCallback but it’s store data instead of a function (array, objects ..etc)
	- it’s  usually used for save a memory intensive to recalculate data 
		- Example: 
		```javascript
		useMemo(()=>, [dependancies])
		```


## Custom Hooks
- it’s a function that use a stateful for manage a state , it’s start with ‘use’ word ex: useHttp() usually we create it for write the common state logic 

## Redux
- Redux is a state management library.
- to use Redux you need to make a communication between (store and reducer) then subscribe the store to a subscriber function
	1. create a reducer function ex: `counterReducer = (state , action) =>{}; `
	2.  create a store  which take a reducer as an argument —> `createStore(counterReducer);`
	- Redux in general need to subscribe and bellow is not on React :
		- create a subscriber function to subscribe to the store —> 
			```javascript
			const storeSubscriber = () => {
  			const latestState = store.getState();
  			console.log(latestState)
			}
			```
		- subscribe to the store —> store.subscribe(storeSubscriber)
	- for subscription inside React project: 
		3. import a provider from “react-redux” in a top level of the application then wrap it with it (index.js)and pass the store into store prop —> ex: `root.render(<Provider store = {store} ><App /></Provider>);`
		4. when you need to use the values inside a component you have to use useSelector hooks provide by “react-redux” then call the value you need ex: `const counter = useSelector(state => state.counter );`
		5. when you need to dispatch —> `import useDispatch() from 'react-redux'` then assign it to a var and use it ex: `const dispatch = useDispatch(); .. then to dispatch —>dispatch({type: 'decrement’,}) ` note that you can pass a payload to the action ex: dispatch({type: 'decrement', amount:5 })

## Redux Toolkit
- Redux Toolkit simplifies the usage of Redux.
- Steps:
	1. inside store you will import `import { createSlice , configureStore} from "@reduxjs/toolkit"`
	2. the createSlice is take an object with name, initialState and reducers which reducers is take 
	another object with all actions —> ex:
	```javascript
		const counterSlice = createSlice({
			name: 'counter',
			initialState,
				reducers: {
						increment(state) {
							state.counter++;
						},
					increase(state, action) {
							state.counter = state.counter + action.payload;
						},
			}
		})
	```
	3. you need to configure store with configureStore() which take an objects with reducer key ex:
	```javascript
		const store = configureStore({
			reducer: counterSlice.reducer
			});
	```
	4. then you export the store and use it inside the provider
	5. and export the actions to import it inside the component and dispatch them there ex: `export const counterActions = counterSlice.actions`
	 */ inside the component file will be :: /*
	 	```javascript
		import { useSelector, useDispatch } from 'react-redux';
		import { counterActions } from './store';
		dispatch(counterActions.increment())
		const counter = useSelector((state)=>state.counter );
	```
	- if you dealing with multiple slices then your configureStore will be like:
		`{reducer: counter: counterSlice.reducer, auth: authSlice.reducer}`


## React Routing
- to start routing inside your application, 
	1. you need to install a new package which call `‘read-router-dom’`
	2. then inside your App.js `import {createBrowserRouter, RouterProvider }`
	3. then create the router by using createBrowserRouter —> 
		`const router = createBrowserRouter ({path: ‘/’, element: <HomePage / >})`
		HomePage: is a component created inside pages folder to render it pn specific path
	4. return RouterProvider with router prop (inside function App) —> `<RouterProvider router ={router}/>`
- alternative way to create router:
	1. import {createBrowserRouter, createRouteFromElements, Route} from ‘read-router-dom’
	2. 
		```javascript
			const routerDefinations =  createRouteFromElements(
									<Route>
										<Route path: ‘/’ element: {<HomePage / >}/>
									</Route>
									)
		```
	3. `const router = createBrowserRouter(routerDefinations)`

-  note: you can use {Link}  from ‘read-router-dom’ instead of <a></a> to prevent send request and navigate between pages `<Link to=‘/path’ >Page Name<Link/>`
- t’s better to use `NavLink` than Link for navigation, because it provide you with more flexibility
	by specific the Active page for example —> `<NavLink to=‘/path’ className= {(isActive)=> isActive && classes.active}>Page Name<NavLink/>`
-  to navigate programmatically `import {useNavigate}  from ‘read-router-dom’ `then use it .

### App Layout 
- to create a layout follow below: 
	1. create	 your Layout component inside pages folder
	2. inside the router you can use children prop to wrap the pages with the layout
		```javascript
			const router = createBrowserRouter (
							{path: ‘/’, 
							element: <RootLayout / >
							children: [{path: ‘/’,  element: <HomePage / >}
									{path: ‘/’products,  element: <ProductsPage / >}
									]
							}
							)
		```
	3. inside the Layout page you need to mark up where the children should render you do it with `{Outlet}from from ‘read-router-dom’` then use it
### Dynamic Route
- You will use params inside your path then useParams inside your component to get the value
	1. inside the router —> `{path: /hello/:id }`
	2. inside the component `import {useParams}from from ‘read-router-dom’ `
	3. const params = `useParams();` then you will have access to the param ex: `params.id`

## Concepts and Terms:	
- Two-way binding
- Controlled and unControlled components
- Styled component (css styling way - package)
- Debouncing
- Cleanup function for useEffect