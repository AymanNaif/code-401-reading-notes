# [React - Conditional Rendering](https://reactjs.org/docs/conditional-rendering.html)

## Conditional Rendering

Conditional rendering in React works the same way conditions work in JavaScript. Use JavaScript operators like if or the conditional operator to create elements representing the current state, and let React update the UI to match them.

## Element Variables

You can use variables to store elements. This can help you conditionally render a part of the component while the rest of the output doesn’t change.

## Inline If with Logical && Operator

You may embed expressions in JSX by wrapping them in curly braces. This includes the JavaScript logical && operator.

## Inline If-Else with Conditional Operator

Another method for conditionally rendering elements inline is to use the JavaScript conditional operator ```condition ? true : false```.

## Preventing Component from Rendering

In rare cases you might want a component to hide itself even though it was rendered by another component. To do this return null instead of its render output.

# [React - Lists & Keys](https://reactjs.org/docs/lists-and-keys.html)

## Rendering Multiple Components

You can build collections of elements and include them in JSX using curly braces ```{}```.

## Basic List Component

Usually you would render lists inside a component.

## Keys

Keys help React identify which items have changed, are added, or are removed.

## Extracting Components with Keys

Keys only make sense in the context of the surrounding array.

## Keys Must Only Be Unique Among Siblings

Keys used within arrays should be unique among their siblings. However they don’t need to be globally unique. 

# [React - Forms](https://reactjs.org/docs/forms.html)

## Forms

HTML form elements work a little bit differently from other DOM elements in React, because form elements naturally keep some internal state.

## Controlled Components

In HTML, form elements such as ```<input>```, ```<textarea>```, and ```<select>``` typically maintain their own state and update it based on user input. In React, mutable state is typically kept in the state property of components, and only updated with setState().

## The textarea Tag

In React, a ```<textarea>``` uses a value attribute instead. This way, a form using a ```<textarea>``` can be written very similarly to a form that uses a single-line input.

## The select Tag

In HTML, ```<select>``` creates a drop-down list.
React, instead of using this selected attribute, uses a value attribute on the root select tag. This is more convenient in a controlled component because you only need to update it in one place. 

## The file input Tag

In HTML, an ```<input type="file">``` lets the user choose one or more files from their device storage to be uploaded to a server or manipulated by JavaScript via the File API.
Because its value is read-only, it is an uncontrolled component in React. It is discussed together with other uncontrolled components later in the documentation.

## Handling Multiple Inputs

When you need to handle multiple controlled input elements, you can add a name attribute to each element and let the handler function choose what to do based on the value of event.target.name.

## Controlled Input Null Value

Specifying the value prop on a controlled component prevents the user from changing the input unless you desire so. If you’ve specified a value but the input is still editable, you may have accidentally set value to undefined or null.

## Alternatives to Controlled Components

It can sometimes be tedious to use controlled components, because you need to write an event handler for every way your data can change and pipe all of the input state through a React component. This can become particularly annoying when you are converting a preexisting codebase to React, or integrating a React application with a non-React library. In these situations, you might want to check out uncontrolled components, an alternative technique for implementing input forms.

## Fully-Fledged Solutions

If you’re looking for a complete solution including validation, keeping track of the visited fields, and handling form submission, Formik is one of the popular choices. However, it is built on the same principles of controlled components and managing state — so don’t neglect to learn them.

# [React - Lifting State](https://reactjs.org/docs/lifting-state-up.html)

## Adding a Second Input

Our new requirement is that, in addition to a Celsius input, we provide a Fahrenheit input, and they are kept in sync.

We can start by extracting a TemperatureInput component from Calculator.

## Writing Conversion Functions
First, we will write two functions to convert from Celsius to Fahrenheit and back:

```
function toCelsius(fahrenheit) {
  return (fahrenheit - 32) * 5 / 9;
}

function toFahrenheit(celsius) {
  return (celsius * 9 / 5) + 32;
}
```

These two functions convert numbers.

# [React - Composition vs Inheritance](https://reactjs.org/docs/composition-vs-inheritance.html)

## Composition vs Inheritance

React has a powerful composition model, and we recommend using composition instead of inheritance to reuse code between components.

## Containment

Some components don’t know their children ahead of time. This is especially common for components like Sidebar or Dialog that represent generic “boxes”.

## Specialization

Sometimes we think about components as being “special cases” of other components. For example, we might say that a WelcomeDialog is a special case of Dialog.

In React, this is also achieved by composition, where a more “specific” component renders a more “generic” one and configures it with props.

## So What About Inheritance?

At Facebook, we use React in thousands of components, and we haven’t found any use cases where we would recommend creating component inheritance hierarchies.

Props and composition give you all the flexibility you need to customize a component’s look and behavior in an explicit and safe way. Remember that components may accept arbitrary props, including primitive values, React elements, or functions.

If you want to reuse non-UI functionality between components, we suggest extracting it into a separate JavaScript module. The components may import it and use that function, object, or a class, without extending it.

# [Thinking in React]

React is, in our opinion, the premier way to build big, fast Web apps with JavaScript. It has scaled very well for us at Facebook and Instagram.

One of the many great parts of React is how it makes you think about apps as you build them.

## Start With A Mock
Imagine that we already have a JSON API and a mock from our designer. 

![mock](https://reactjs.org/static/1071fbcc9eed01fddc115b41e193ec11/d4770/thinking-in-react-mock.png)

JSON API returns some data
```
[
  {category: "Sporting Goods", price: "$49.99", stocked: true, name: "Football"},
  {category: "Sporting Goods", price: "$9.99", stocked: true, name: "Baseball"},
  {category: "Sporting Goods", price: "$29.99", stocked: false, name: "Basketball"},
  {category: "Electronics", price: "$99.99", stocked: true, name: "iPod Touch"},
  {category: "Electronics", price: "$399.99", stocked: false, name: "iPhone 5"},
  {category: "Electronics", price: "$199.99", stocked: true, name: "Nexus 7"}
];
```

## Step 1: Break The UI Into A Component Hierarchy

The first thing you’ll want to do is to draw boxes around every component (and subcomponent) in the mock and give them all names. If you’re working with a designer, they may have already done this, so go talk to them! Their Photoshop layer names may end up being the names of your React components!

We have five components in our app. We’ve italicized the data each component represents.

1. **FilterableProductTable (orange):** contains the entirety of the example
2. **SearchBar (blue):** receives all user input
3. **ProductTable (green):** displays and filters the data collection based on user input
4. **ProductCategoryRow (turquoise):** displays a heading for each category
5. **ProductRow (red):** displays a row for each product

## Step 2: Build A Static Version in React

Now that you have your component hierarchy, it’s time to implement your app. The easiest way is to build a version that takes your data model and renders the UI but has no interactivity. It’s best to decouple these processes because building a static version requires a lot of typing and no thinking, and adding interactivity requires a lot of thinking and not a lot of typing. We’ll see why.

To build a static version of your app that renders your data model, you’ll want to build components that reuse other components and pass data using props. props are a way of passing data from parent to child. If you’re familiar with the concept of state, don’t use state at all to build this static version. State is reserved only for interactivity, that is, data that changes over time. Since this is a static version of the app, you don’t need it.

You can build top-down or bottom-up. That is, you can either start with building the components higher up in the hierarchy (i.e. starting with FilterableProductTable) or with the ones lower in it (ProductRow). In simpler examples, it’s usually easier to go top-down, and on larger projects, it’s easier to go bottom-up and write tests as you build.

## Step 3: Identify The Minimal (but complete) Representation Of UI State

To make your UI interactive, you need to be able to trigger changes to your underlying data model. React achieves this with state.

To build your app correctly, you first need to think of the minimal set of mutable state that your app needs. The key here is DRY: Don’t Repeat Yourself. Figure out the absolute minimal representation of the state your application needs and compute everything else you need on-demand. For example, if you’re building a TODO list, keep an array of the TODO items around; don’t keep a separate state variable for the count. Instead, when you want to render the TODO count, take the length of the TODO items array.

## Step 4: Identify Where Your State Should Live

We’ve identified what the minimal set of app state is. Next, we need to identify which component mutates, or owns, this state.

Remember: React is all about one-way data flow down the component hierarchy. It may not be immediately clear which component should own what state. This is often the most challenging part for newcomers to understand, so follow these steps to figure it out:

For each piece of state in your application:

- Identify every component that renders something based on that state.
- Find a common owner component (a single component above all the components that need the state in the hierarchy).
- Either the common owner or another component higher up in the hierarchy should own the state.
- If you can’t find a component where it makes sense to own the state, create a new component solely for holding the state and add it somewhere in the hierarchy above the common owner component.

Let’s run through this strategy for our application:

- ProductTable needs to filter the product list based on state and SearchBar needs to display the search text and checked state.
- The common owner component is FilterableProductTable.
- It conceptually makes sense for the filter text and checked value to live in FilterableProductTable

Cool, so we’ve decided that our state lives in FilterableProductTable. First, add an instance property this.state = {filterText: '', inStockOnly: false} to FilterableProductTable’s constructor to reflect the initial state of your application. Then, pass filterText and inStockOnly to ProductTable and SearchBar as a prop. Finally, use these props to filter the rows in ProductTable and set the values of the form fields in SearchBar.

## Step 5: Add Inverse Data Flow

So far, we’ve built an app that renders correctly as a function of props and state flowing down the hierarchy. Now it’s time to support data flowing the other way: the form components deep in the hierarchy need to update the state in FilterableProductTable.

React makes this data flow explicit to help you understand how your program works, but it does require a little more typing than traditional two-way data binding.

If you try to type or check the box in the current version of the example, you’ll see that React ignores your input. This is intentional, as we’ve set the value prop of the input to always be equal to the state passed in from FilterableProductTable.

We want to make sure that whenever the user changes the form, we update the state to reflect the user input. Since components should only update their own state, FilterableProductTable will pass callbacks to SearchBar that will fire whenever the state should be updated. We can use the onChange event on the inputs to be notified of it. The callbacks passed by FilterableProductTable will call setState(), and the app will be updated.
