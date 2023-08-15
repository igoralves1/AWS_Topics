### Understanding Node.js module resolution
[Optimizing Node.js dependencies in AWS Lambda](https://aws.amazon.com/blogs/compute/optimizing-node-js-dependencies-in-aws-lambda/)
[Modular packages in AWS SDK for JavaScript]()

When you require or import a resource in your code, Node.js tries to resolve that resource by either the file- or directory name, or in the node_modules directory. Once it finds the resource, it is loaded from disk, parsed and run.

If that file or dependency in turn contains other imports or require statements, the process repeats, which causes disk reads. The more dependencies and files that are imported in a function, the longer it takes to initialize.

This only impacts imported and used code. Including files in a project that are not imported or used has minimal effect on startup performance.

You should also evaluate what’s being imported. Even though modern JavaScript bundlers such as esbuild, Rollup, or WebPack uses tree shaking and dead code elimination, importing dependencies via wildcard, global-, or top-level imports can result in larger bundles.
