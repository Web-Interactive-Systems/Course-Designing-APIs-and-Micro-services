---
type: NoteCard
tags: []
---

# NodeJS Working With Packages

NodeJS packages are librairies that other developers created and made available for the community.

We can find and download packages from different sources. Some of them are:

*   **Registries**: are collections of packages, like the npm registry (<https://www.npmjs.com/>). You can also host your own registry.
*   **Repositories**: like GitHub, we can install packages directly using the URL of a repository on GitHub.
*   **Files**: We can install packages from local folders or zipped files, useful for testing our own packages.
*   **Directories**: we can also install a package directly from a directory.

## Choosing a Dependency

Always look for dependencies that are open source and actively maintained. Github is a good place to find good dependencies. Also, it is good practice to look for dependencies with less to zero dependencies. By doing so you:

*   Minimize the bundle size
*   Lower the risque of conflict between dependencies
*   Lower the risque of dependencies becoming obsolete

Other considerations include:

*   **Popularity**: A package's popularity can indicate its quality
*   **Licensing**: If you plan to sell your software, ensure all dependency package licenses allow for reuse and resell

## Installing a Package

To install a package use the command \`install\`

```js
npm install <package-name>

// or

npm i <package-name>
```

When you run the npm  `install` command, the npm connects to a global registry (npmjs.com), fetches the package, and places it inside the `node_modules` folder at the root of your project. This command will the package as a dependency. The dependency will be added to the file package.json.

To install a package as a dev dependency, add the arugment \`—save-dev\`

```js
npm i <package-name> --save-dev

// or 

npm i <package-name> -D
```

## NPM Help

NPM has a hepler utility using the command \`—help\`:

```js
npm --help
```

