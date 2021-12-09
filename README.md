# MY_FIRST_WEB_APP
This project is built for the CSC190 senior software project course using Svelte

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Svelte is a useful tool for building web applications. It converts app into ideal JavaScript at build time, rather than interpreting application code at run time. 
You can built your entire app with Svelte, or you can add it incrementally to an existing codebase.

Svelte sticks closely to the classic web development model of 

- HTML
- CSS
- JavaScript
- ✨Magic ✨

## Application structure
The starter template comes with the following structure:

- moz-todo-svelte
    - node_modules
    - public
    - scripts
    - src
      - App.svelte: this is the file where I had all my codes for this project
    - .gitignore
    - package-lock.json
    - package.json
    - README.md
    - rollup.config.js
    
## Create first Svelte app
Download the starter template application...

```sh
npx degit sveltejs/template moz-todo-svelte
```

Create starter app template...

```sh
cd moz-todo-svelte
npm install
npm run dev
```

Svelte will compile and build the appliaction. It will start a local server at **localhost:5000**.

Svelte will watch for file updates, and automatically recompile and refresh the app for you when changes are made in Visual Studio Code.

## License

MIT
