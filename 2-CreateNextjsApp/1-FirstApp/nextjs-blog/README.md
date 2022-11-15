# Notes

## Link Component

The Link component is similar to using `<a>` tags, but instead of `<a href="…">`, you use `<Link href="…">`.

> **Note**: Before Next.js 12.2, it was required that the Link component wrapped an `<a>` tag, but this is not required in versions 12.2 and above.

The Link component enables client-side navigation between two pages in the same Next.js app.

Furthermore, in a production build of Next.js, whenever Link components appear in the browser’s viewport, Next.js automatically prefetches the code for the linked page in the background. By the time you click the link, the code for the destination page will already be loaded in the background, and the page transition will be near-instant!


## Assets

Next.js can serve static assets, like images, under the top-level public directory. Files inside public can be referenced from the root of the application similar to pages.

The public directory is also useful for robots.txt, Google Site Verification, and any other static assets. Check out the documentation for [Static File Serving](https://nextjs.org/docs/basic-features/static-file-serving) to learn more.

### Related Reading

* [next/link](https://nextjs.org/docs/api-reference/next/link)
* [Routing](https://nextjs.org/docs/routing/introduction)
* [Image Component and Image Optimization](https://nextjs.org/docs/basic-features/image-optimization)
