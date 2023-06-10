React Notes: 
- To lifting state up the data from child to parent
	1- define a function in the parent to get the value 
		ex: const getDate = (enterdData) =>{
							const data = enterdData
										}
	2- then pass this function to the child as a prop ex <childComp savedData = {getDate} />
	3- call the function inside child as a prop ex: props.savedData(theDataPassed)
- Portal: is to render a component in deferent place in the Dom
Hooks:
- useRef():
	The primary use case for useRef is to access or store references to DOM elements or other mutable 
	values without triggering a re-render. Unlike useState, updating the value stored in a useRef does not 	cause the component to re-render.(usually used for input field ex: <input ref={inputRef} type="text" /
- useEffect:
	 This hook allows you to perform side effects in functional components, such as fetching data,
	subscribing to events, or manipulating the DOM. It takes a function as its first parameter, which will be 	executed after every render. You can also provide a cleanup function that will be executed before the 	component is unmounted.
  - useReducer(): 
	The useReducer hook is another built-in hook provided by React. It is used for managing complex state 	logic in functional components. While the useState hook is suitable for managing simple state, 
	the useReducer hook provides a more powerful alternative when you need to handle state transitions 	that involve multiple actions and complex state updates.
	The useReducer hook follows the concept of a reducer function, which is a pure function that takes the 	current state and an action as arguments, and returns the new state based on the action. The reducer 	function specifies how state transitions should happen in response to different actions.
	The useReducer hook is another built-in hook provided by React. It is used for managing complex state 	logic in functional components. While the useState hook is suitable for managing simple state, 
	the useReducer hook provides a more powerful alternative when you need to handle state transitions 
	that involve multiple actions and complex state updates.
	The useReducer hook follows the concept of a reducer function, which is a pure function that takes the 	current state and an action as arguments, and returns the new state based on the action. The reducer 	function specifies how state transitions should happen in response to different actions. For ex check 
	chatGPT
	- useContext():
		Context provides a way to share data between components without explicitly passing it through 
		every level of the component tree. It is useful when you have data that needs to be accessed by 
		multiple components at different levels.
		
		to apply that:
			1- createContext(); —> const MyContext = createContext();
			2- create a provider component  and export it—> 
				function MyProvider({ children }) {
 						const value = 'Hello, World!';
				 		 return <MyContext.Provider value={value}>{children}</MyContext.Provider>;							}
			3- wrap the component you need to provide it with a data with the provider
			4- useContext —>   const value = useContext(MyContext);
			5- use the value of it :D
	- React.memo(component)
        * is a higher-order component (HOC) used to memoize the rendering of a functional component.
        * It is typically used to optimize the rendering performance of a functional component by preventing unnecessary re-renders.
        * It takes a component as an argument and returns a new memoized component.
        * The memoized component will only re-render if its props have changed.
	-  useCallback
		hook is used to store a function across component execution (save a function) to prevent 
		re-creation on every component re-render — so one function is create and store on a memory
		it take a dependancies such as useEffect and re-create it when dependancies is changed ex: 			useCallback(()=>, [dependancies])
	-  useMemo 
		is a hook such as  useCallback but it’s store data instead of a function (array, objects ..etc) it’s  	
 		usually used for save a memory intensive to recalculate data ex: useMemo(()=>, [dependancies])

Redux:
	to use Redux you need to make a communication between (store and reducer) then subscribe the store 	to a subscriber function
	1- create a reducer function ex: counterReducer = (state , action) =>{}; 
	2- create a store  which take a reducer as an argument —> createStore(counterReducer);
	= Redux in general need to subscribe and bellow is not on React :
		- create a subscriber function to subscribe to the store —> 
			const storeSubscriber = () => {
  			const latestState = store.getState();
  			console.log(latestState)
			}
		- subscribe to the store —> store.subscribe(storeSubscriber)
	=for subscription inside React project: 
	3- import a provider from “react-redux” in a top level of the application then wrap it with it (index.js)
	    and pass the store into store prop —> ex: root.render(<Provider store = {store} ><App /></Provider>);
	4- when you need to use the values inside a component you have to use useSelector hooks provide by 
	“react-redux” then call the value you need ex:   const counter = useSelector(state => state.counter );
	5- when you need to dispatch —> import useDispatch() from 'react-redux' then assign it to a var and 
	use it ex: const dispatch = useDispatch(); .. then to dispatch —>dispatch({type: 'decrement’,}) note 
	that you can pass a payload to the action ex: dispatch({type: 'decrement', amount:5 })
Redux toolkit:
	it’s easier the using of redux all you need is: 
	1- inside store you will import import { createSlice , configureStore} from "@reduxjs/toolkit"
	2- the createSlice is take an object with name, initialState and reducers which reducers is take 
	another object with all actions —> ex: 
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
	3- you need to configure store with configureStore() which take an objects with reducer key
	ex: const store = configureStore({
 		 reducer: counterSlice.reducer
		});
	4- then you export the store and use it inside the provider
	5- and export the actions to import it inside the component and dispatch them there
	ex: export const counterActions = counterSlice.actions
	*/ inside the component file will be :: /*
	import { useSelector, useDispatch } from 'react-redux';
	import { counterActions } from './store';
    	dispatch(counterActions.increment())
	const counter = useSelector((state)=>state.counter );
	- if you dealing with multiple slices then your configureStore will be like:
		{reducer: counter: counterSlice.reducer, auth: authSlice.reducer}





 

Concepts and Terms:	
- Two-way binding
- Controlled and unControlled components
- Styled component (css styling way - package)
- Debouncing
- Cleanup function for useEffect
