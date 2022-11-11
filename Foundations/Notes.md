#Introduction

This tutorial assumes knowledge of HTML, CSS, JavaScript, and no knowledge of React. 

Next.js is a flexible React framework that gives you building blocks to create fast web applications. By framework, we mean Next.js handles the tooling and configuration needed for React, and provides additional structure, features, and optimizations for your application.

 There are a few things you need to consider when building modern applications. Such as:

**User Interface** - how users will consume and interact with your application.
**Routing** - how users navigate between different parts of your application.
**Data Fetching** - where your data lives and how to get it.
**Rendering** - when and where you render static or dynamic content.
**Integrations** - what third-party services you use (CMS, auth, payments, etc) and how you connect to them.
**Infrastructure** - where you deploy, store, and run your application code (Serverless, CDN, Edge, etc).
**Performance** - how to optimize your application for end-users.
**Scalability** - how your application adapts as your team, data, and traffic grow.
**Developer Experience** - your team’s experience building and maintaining your application.

![](https://nextjs.org/static/images/learn/foundations/next-app.png)

# From JavaScript to React

The browser reads the HTML and constructs the Document Object Model (DOM).
![The browser reads the HTML and constructs the Document Object Model (DOM).](https://nextjs.org/static/images/learn/foundations/html-to-dom.png)

**What is the DOM?**

The DOM is an object representation of the HTML elements. It acts as a bridge between your code and the user interface, and has a tree-like structure with parent and child relationships.

![](https://nextjs.org/static/images/learn/foundations/dom-to-ui.png)

You can use DOM methods and a programming language, such as JavaScript, to listen to user events and manipulate the DOM by selecting, adding, updating, and deleting specific elements in the user interface. DOM manipulation allows you to not only target specific elements, but also change their style and content.

**Additional Resources:**

[Introduction to the DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
[How to view the DOM in Google Chrome](https://developer.chrome.com/docs/devtools/dom/)
[How to view the DOM in Firefox](https://developer.mozilla.org/en-US/docs/Tools/Debugger/How_to/Highlight_and_inspect_DOM_nodes)
