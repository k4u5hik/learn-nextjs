# Essential JavaScript for React

------------------------------

While you can learn JavaScript and React at the same time, being familiar with JavaScript can make the process of learning React easier.

In the next sections, you will be introduced to some core concepts of React from a JavaScript perspective. Here’s a summary of the JavaScript topics that will be mentioned:

**[Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)** and **[Arrow Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)**
**[Objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)**
**[Arrays and array methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)**
**[Map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map)**
**[Destructuring](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)**
**[Template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)**
**[Ternary Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)**
**[ES Modules and Import / Export Syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)**

While this course does not dive into JavaScript, it’s good practice to stay up to date with the latest versions of JavaScript. But if you don’t feel proficient in JavaScript yet, don’t let this hinder you from starting to build with React!

## React Core Concepts

There are three core concepts of React that you'll need to be familiar with to start building React applications. These are:

**1) Components
2) Props
3) State**

* React components should be capitalized to distinguish them from plain HTML and JavaScript.
* Second, you use React components the same way you’d use regular HTML tags, with angle brackets `<>`.

## Using variables in JSX

To use the variable you defined, you can use curly braces {}, a special JSX syntax that allows you to write regular JavaScript directly inside your JSX markup.

You can add any JavaScript expression (something that evaluates to a single value) inside curly braces. For example:

1) An object property with dot notation.

```jsx
   function Header(props) {
  return <h1>{props.title}</h1>;
}
```

2) A template literal:

```jsx
function Header({ title }) {
  return <h1>{`Cool ${title}`}</h1>;
}
```

3) The returned value of a function.

```jsx
function createTitle(title) {
  if (title) {
    return title;
  } else {
    return 'Default title';
  }
}

function Header({ title }) {
  return <h1>{createTitle(title)}</h1>;
}
```

4) Or ternary operators.

```jsx
function Header({ title }) {
  return <h1>{title ? title : 'Default Title'}</h1>;

  function Page() {
  return (
    <div>
      <Header title="React 💙" />
      <Header title="A new title" />
    </div>
  );
}
}
```

5) Iterating through lists

```jsx
function HomePage() {
  const names = ['Ada Lovelace', 'Grace Hopper', 'Margaret Hamilton'];

  return (
    <div>
      <Header title="Develop. Preview. Ship. 🚀" />
      <ul>
        {names.map((name) => (
          <li>{name}</li>
        ))}
      </ul>
    </div>
  );
}
```

**If you run this code, React will give us a warning about a missing `key` prop.** This is because React needs something to uniquely identify items in an array so it knows which elements to update in the DOM.

You can use the names for now since they are currently unique, but it's recommended to use something guaranteed to be unique, like an item ID.

6) You can then use the `array.map()` method to iterate over the array and use an arrow function to map a name to a list item

```jsx
function HomePage() {
  const names = ['Ada Lovelace', 'Grace Hopper', 'Margaret Hamilton'];

  return (
    <div>
      <Header title="Develop. Preview. Ship. 🚀" />
      <ul>
        {names.map((name) => (
          <li key={name}>{name}</li>
        ))}
      </ul>
    </div>
  );
}
```

## Additional Resources for React props and rendering

**[Passing props to a component](https://beta.reactjs.org/learn/passing-props-to-a-component)**
**[Rendering lists](https://beta.reactjs.org/learn/rendering-lists)**
**[Conditional rendering](https://beta.reactjs.org/learn/conditional-rendering)**

## Adding Interactivity with State

Let’s create a like button inside your `HomePage` component. First, add a button element inside the `return()` statement. To make the button do something when clicked, you can make use of the `onClick` event.

```jsx
<button onClick={handleClick}>Like</button>
```

**In React, event names are camelCased.** The `onClick` event is one of many possible events you can use to respond to user interaction. For example, you can use `onChange` for input fields or `onSubmit` for forms.

## State and Hooks

<span style="color:red">❗ React has a set of functions called [hooks](https://reactjs.org/docs/hooks-intro.html). Hooks allow you to add additional logic such as **state** to your components.</span> 
You can think of state as any information in your UI that changes over time, usually triggered by user interaction.

```jsx
function HomePage() {
  const [likes, setLikes] = React.useState(0);
}
```

`useState()` returns an array, and you can access and use those array values inside your component using **array destructuring**.
The first item in the array is the state `value`, which you can name anything. It’s recommended to name it something descriptive.
The second item in the array is a function to `update` the value. You can name the update function anything, but it's common to prefix it with `set` followed by the name of the state variable you’re updating.
You can also take the opportunity to add the initial value of your likes state: zero. Then, you can check the initial state is working by using the state variable inside your component.

```jsx
function HomePage() {
  // ...
  const [likes, setLikes] = React.useState(0);

  return (
    // ...
    <button onClick={handleClick}>Like({likes})</button>
  );
}
```

Finally, you can call your state updater function, `setLikes` in your `HomePage` component, let's add it inside the `handleClick()` function you previously defined:

```jsx
function HomePage() {
  // ...
  const [likes, setLikes] = React.useState(0);

  function handleClick() {
    setLikes(likes + 1);
  }

  return (
    <div>
      {/* ... */}
      <button onClick={handleClick}>Likes ({likes})</button>
    </div>
  );
}
```

Clicking the button will now call the handleClick function, which calls the setLikes state updater function with a single argument of the current number of likes + 1.

**Note:** Unlike props which are passed to components as the first function parameter, the state is initiated and stored within a component. You can pass the state information to children components as props, but the logic for updating the state should be kept within the component where state was initially created.

## Additional Resources for React State

[Adding Interactivity](https://beta.reactjs.org/learn/adding-interactivity)
[Managing State](https://beta.reactjs.org/learn/managing-state)
[State: A Component's Memory](https://beta.reactjs.org/learn/state-a-components-memory#)
[Meet your first Hook](https://beta.reactjs.org/learn/state-a-components-memory#meet-your-first-hook)
[Responding to Events](https://beta.reactjs.org/learn/responding-to-events)
[How React handles renders](https://beta.reactjs.org/learn/render-and-commit)
[How to use refs](https://beta.reactjs.org/learn/referencing-values-with-refs)
[How to manage State](https://beta.reactjs.org/learn/managing-state)
[How to use context for deeply nested data](https://beta.reactjs.org/learn/passing-data-deeply-with-context)
[How to use React API hooks](https://beta.reactjs.org/reference)
