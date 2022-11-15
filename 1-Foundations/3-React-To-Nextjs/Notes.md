# Nextjs Core Concepts

## Development and Production Environments

During development, you’re building and running the application on your local machine. Going to production is the process of making your application ready to be deployed and consumed by users.

The application code needs to be compiled, bundled, minified, and code split.

### Compiler

Compiling refers to the process of taking code in one language and outputting it in another language or another version of that language.

![Compiler Image](https://nextjs.org/static/images/learn/foundations/compiling.png)

Next.js has a compiler written in Rust, a low-level programming language, and SWC (Speedy Web Compiler), a platform that can be used for compilation, minification, bundling, and more.

### Minifying

Minification is the process of removing unnecessary code formatting and comments without changing the code’s functionality. The goal is to improve the application’s performance by decreasing file sizes.

![Minifying Image](https://nextjs.org/static/images/learn/foundations/minifying.png)

### Bundling

Bundling is the process of combining multiple files into a single file. This is done to improve performance by reducing the number of requests to the server.

![Bundling Image](https://nextjs.org/static/images/learn/foundations/bundling.png)

Bundling is also the process of resolving the web of dependencies and merging (or ‘packaging’) the files (or modules) into optimized bundles for the browser, with the goal of reducing the number of requests for files when a user visits a web page.

### Code Splitting

Code splitting is the process of splitting your code into multiple bundles that can be loaded on demand or in parallel. The goal is to improve the application's initial load time by only loading the code required to run that page.

![Code Splitting Image](https://nextjs.org/static/images/learn/foundations/code-splitting.png)

* Any code shared between pages is also split into another bundle to avoid re-downloading the same code on further navigation.
* After the initial page load, Next.js can start [pre-loading](https://nextjs.org/docs/api-reference/next/link) the code of other pages users are likely to navigate to.
* [Dynamic imports](https://nextjs.org/docs/advanced-features/dynamic-import) are another way to manually split what code is initially loaded.

### Build Time and Runtime

**Build time** is the time it takes to compile, bundle, and minify your code. Build time (or build step) is the name given to a series of steps that prepare your application code for production.

**Runtime** is the time it takes to load your code and execute it. Runtime (or request time) refers to the period of time when your application runs in response to a user’s request, after your application has been built and deployed.

### What is Rendering?

There is an unavoidable unit of work to convert the code you write in React into the HTML representation of your UI. This process is called rendering.

Rendering can take place on the server or on the client. It can happen either ahead of time at build time, or on every request at runtime.

With Next.js, three types of rendering methods are available: **Server-Side Rendering**, **Static Site Generation**, and **Client-Side Rendering**.

#### Pre-Rendering

Server-Side Rendering and Static Site Generation are also referred to as Pre-Rendering because the fetching of external data and transformation of React components into HTML happens before the result is sent to the client.

#### Client-Side Rendering vs. Pre-Rendering

In a standard React application, the browser receives an empty HTML shell from the server along with the JavaScript instructions to construct the UI. This is called client-side rendering because the initial rendering work happens on the user's device.

![Client-Side Rendering Image](https://nextjs.org/static/images/learn/foundations/client-side-rendering.png)

>**Note**: You can opt to use client-side rendering for specific components in your Next.js application by choosing to fetch data with React’s useEffect() or a data fetching hook such as [useSWR](https://swr.vercel.app/).

In contrast, **Next.js pre-renders every page by default.** Pre-rendering means the HTML is generated in advance, on a server, instead of having it all done by JavaScript on the user's device.

**In practice, this means that for a fully client-side rendered app, the user will see a blank page while the rendering work is being done.** **Compared to a pre-rendered app, where the user will see the constructed HTML**:

![Client-Side Rendering vs. Pre-Rendering Image](https://nextjs.org/static/images/learn/foundations/pre-rendering.png)

### Server-Side Rendering

With server-side rendering, the HTML of the page is generated on a server for **each** request. The generated HTML, JSON data, and JavaScript instructions to make the page interactive are then sent to the client.

On the client, the HTML is used to show a fast non-interactive page, while React uses the JSON data and JavaScript instructions to make components interactive (for example, attaching event handlers to a button). ==This process is called **hydration**.==

**In Next.js, you can opt to server-side render pages by using [getServerSideProps](https://nextjs.org/docs/basic-features/data-fetching/get-server-side-props).**

>**Note**: React 18 and Next 12 introduce an alpha version of React server components. **Server components are completely rendered on the server and do not require client-side JavaScript to render.** In addition, server components allow developers to keep some logic on the server and only send the result of that logic to the client. This reduces the bundle size sent to the client and improves client-side rendering performance. Learn more about React server components here.

**Static Site Generation**
With Static Site Generation, the HTML is generated on the server, but unlike server-side rendering, there is no server at runtime. Instead, content is generated once, at build time, when the application is deployed, and the HTML is stored in a CDN and re-used for each request.

In Next.js, you can opt to statically generate pages by using [getStaticProps](https://nextjs.org/docs/basic-features/data-fetching/get-static-props).

>**Note**: You can use [Incremental Static Regeneration](https://nextjs.org/docs/basic-features/data-fetching/incremental-static-regeneration) to create or update static pages after you’ve built your site. This means you do not have to rebuild your entire site if your data changes.

To learn more about which rendering method is right for your specific use case, see the [data fetching docs](https://nextjs.org/docs/basic-features/data-fetching/overview).

### The Edge

The Edge is a generalized concept for the fringe (or edge) of the network, closest to the user. CDNs could be considered part of "the Edge" because they store static content at the fringe (edge) of the network.

Similar to CDNs, Edge servers are distributed to multiple locations around the world. But unlike CDNs, which store static content, some Edge servers can run code.

**This means both caching and code execution can be done at the Edge closer to the user**.

By running code at the Edge, you can move some of the work that was traditionally done client-side or server-side to the Edge ([see examples with Next.js here](https://vercel.com/features/edge-functions#:~:text=or%20steps%20required.-,CODE%20EXAMPLES,-Unlock%20the%20potential)). This can make your application more performant because it reduces the amount of code sent to the client, and part of the user's request does not have to go all the way back to the origin server - thus reducing latency.

In Next.js, you can run code at the Edge with [Middleware](https://nextjs.org/docs/middleware), and soon with [React Server Components](https://nextjs.org/docs/advanced-features/react-18/overview#react-server-components-alpha).
