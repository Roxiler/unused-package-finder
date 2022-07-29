# unused-package

**unused-package is a dependency analysing tool which lets you know which packages are not being used or if package is devDependency but installed as normal dependency**

# Installation

Using npm

```
npm install unused-package --save-dev
```

Using yarn

```
yarn add --dev unused-package 
```

# Usage

**create a file named unused.js in root directory with below code**

```
const check = require("unused-package");

check({ entries: ['entry path to your code'] }).then((res) => {
  console.log(res) // list of packages returned by library
});

Example:
//for react projects
check({ entries: ['src'] }).then((res) => {
  console.log(res)
});

//for next.js projects
check({ entries: ['pages','src','components','next.config.js'] }).then((res) => {
  console.log(res)
});
```

# Note:

- if your code has mutiple entry paths, you can pass all entry points as array form to entries parameter
- library returns the list of packages in array format. listed packages maybe not being used in code, or if devDependency is installed as normal dependency.

**Include unused.js file in your build script to check for extra packages before every build step in package.json**

```
Example:
//for react projects
"scripts":{
   "build": " node unused.js && react-scripts build",
}
//for next.js projects
"scripts":{
   "build": " node unused.js && next build",
}
```

**OR**

**create a seperate script to run unused.js file**

```
"scripts":{
  "detect:unused:packages": " node unused.js"
}

```

**Note: Currently package is still in initial phase and if library returns and false positives please feel free to open an issue**
