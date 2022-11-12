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

## Additional Resources

**[Passing props to a component](https://beta.reactjs.org/learn/passing-props-to-a-component)**
**[Rendering lists](https://beta.reactjs.org/learn/rendering-lists)**
**[Conditional rendering](https://beta.reactjs.org/learn/conditional-rendering)**