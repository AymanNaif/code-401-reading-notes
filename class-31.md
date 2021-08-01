# React 1
## [ES6 Syntax and Feature Overview]

## Variables and constant feature comparison

|  **Keyword**  |    **Scope**    |   **Hoisting**   |   **Can Be Reassigned**   |   **Can Be Redeclared**   |
|:-------------:|:---------------:|:----------------:|:-------------------------:|:-------------------------:|
|   ```var```	| Function scope  |    	  Yes   	 |             Yes	         |           Yes             |
|   ```let```	| Block scope	  |        No      	 |             Yes         	 |            No             |
|  ```const```  | Block scope	  |        No        |	            No	         |            No             |

## Variable declaration

ES6 introduced the ```let``` keyword, which allows for block-scoped variables which cannot be hoisted or redeclared.

## Constant declaration

ES6 introduced the ```const``` keyword, which cannot be redeclared or reassigned, but is not immutable.

## Arrow functions
The arrow function expression syntax is a shorter way of creating a function expression. Arrow functions do not have their own ```this```, do not have prototypes, cannot be used for constructors, and should not be used as object methods.

## Template literals

- **Concatenation/string interpolation**
  - Expressions can be embedded in template literal strings.
- **Multi-line strings**
  - Using template literal syntax, a JavaScript string can span multiple lines without the need for concatenation.
- **Implicit returns**
  - The ```return``` keyword is implied and can be omitted if using arrow functions without a block body.
- **Key/property shorthand**
  - ES6 introduces a shorter notation for assigning properties to variables of the same name.
- **Method definition shorthand**
  - The ```function``` keyword can be omitted when assigning methods on an object.
- **Destructuring (object matching)**
  - Use curly brackets to assign properties of an object to their own variable.
- **Array iteration (looping)**
  - A more concise syntax has been introduced for iteration through arrays and other iterable objects.  
- **Default parameters**
  - Functions can be initialized with default parameters, which will be used only if an argument is not invoked through the function.
- **Spread syntax**
  - Spread syntax can be used to expand an array.
  - Spread syntax can be used for function arguments.
- **Classes/constructor functions**
  - ES6 introducess the ```class``` syntax on top of the prototype-based constructor function.
- **Inheritance**
  - The ```extends``` keyword creates a subclass.
- **Modules - export/import**
  - Modules can be created to export and import code between files.
- **Promises/Callbacks**
  - Promises represent the completion of an asynchronous function. They can be used as an alternative to chaining functions.

# [React - Hello World](https://reactjs.org/docs/hello-world.html)

## Hello World

**The smallest React example looks like this:**
```
ReactDOM.render(
  <h1>Hello, world!</h1>,
  document.getElementById('root')
);
```
# [React - JSX](https://reactjs.org/docs/introducing-jsx.html)

## Why JSX?

React embraces the fact that rendering logic is inherently coupled with other UI logic: how events are handled, how the state changes over time, and how the data is prepared for display.

Instead of artificially separating technologies by putting markup and logic in separate files, React separates concerns with loosely coupled units called “components” that contain both.

React doesn’t require using JSX, but most people find it helpful as a visual aid when working with UI inside the JavaScript code. It also allows React to show more useful error and warning messages.

# [React - Rendering Elements](https://reactjs.org/docs/rendering-elements.html)

To render a React element into a root DOM node, pass both to ```ReactDOM.render()```

# [React - Components & Props](https://reactjs.org/docs/components-and-props.html)

## Components and Props

Components let you split the UI into independent, reusable pieces, and think about each piece in isolation. This page provides an introduction to the idea of components. 

Components are like JavaScript functions. They accept arbitrary inputs (called “props”) and return React elements describing what should appear on the screen.

## Function and Class Components

```
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```
This function is a valid React component because it accepts a single “props” (which stands for properties) object argument with data and returns a React element. We call such components “function components” because they are literally JavaScript functions.

## Composing Components

Components can refer to other components in their output. This lets us use the same component abstraction for any level of detail. A button, a form, a dialog, a screen: in React apps, all those are commonly expressed as components.

## Props are Read-Only

Whether you declare a component as a function or a class, it must never modify its own props.

# [React - State & Lifecycle](https://reactjs.org/docs/state-and-lifecycle.html)

# [React - Handling Events](https://reactjs.org/docs/handling-events.html)
