## Reference https://blog.logrocket.com/guide-performance-optimization-webpack/

### The key to integrate performance optimization into your project is to understand some basic concepts, such as tree shaking, code splitting, and cache busting with `[contenthash]`)

We should separate vendor bundles from our app bundles for caching purposes. Your application code simply changes more often than the vendor code because you adjust versions of your dependencies less frequently.

We can split bundle by

- manually split entry points in config file with htmlWebpackPlugin. This gives us MPA
- dynamic imports and code splitting by route. This gives us SPA and an ability to lazy-load

Lazyload causes the page to flick because it loads new script. But it’s not full page load. ( the full-page-load loads entire sources - html, css, js )

- Code splitting is based on heuristics that find candidates for splitting based on module duplication count and module category
- The default behavior is that only dependencies of ≥30KB are picked as candidates for the vendor bundle
- Sometimes webpack intentionally duplicates code in bundles to minimize requests for additional bundles

Consolidate shared code into common bundles to:

- Minimize bundle size
- Efficient caching

A manifest file describes essential information about your app. In terms of webpack, webpack manifest file describes how to bundle, load or split modules. Essentially, how to interact with modules.

We can reduce bundle size by extracting react and react-dom from our bundles
`Optimization.minimize: true` removes unused code with tree shaking technique (Default behavior of webpack v4 or above)

Tree shaking is a dead code elimination technique that finds and strips that unused code from your bundles. (Default behavior of webpack v4 or above)

Define a performance budget which throws error when assets exceeds a specified threshold size. (For a good development culture purpose)

Use tree-shakeable third-party libraries
