# Node.js

## What is Node.js?
* "Node.js is a JavaScript runtime built on Chrome's V8 JavaScript engine."
* "Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient."
* "Node.js' package ecosystem, npm, is the largest ecosystem of open source libraries in the world."

## Usage
Running js script:
```
node my-script.js
```

### Exercise
Create a folder `node` in `week1`. In the folder create file `script.js` that logs 'This is JavaScript' to console, and run it. 

## npm
* npm (Node Package Manager) is the package manager for Node.js
* Has the most modules of any package manager for any language
* Comes along with Node.js when installed
* Available on command line with npm command
* Can update itself with 
```
npm install -g npm
```

## Global vs. local packages
Global packages:

* Installed globally with -g switch for npm install
* Provide some command-line commands
* e.g.
  ```
  npm install -g angular-cli
  ng new MY_PROJECT
  ```

Local packages

* Installed to the node_modules folder under current folder
* Available only for the current project with require
* e.g.
  ```
  npm install underscore
  ```
  ```javascript
  // in js file:
  const _ = require('underscore')
  ```

### Exercise
#### Global package
Install [nodemon](https://nodemon.io/) globally (package name: nodemon) and use it to automatically reload previously created `script.js` every time you update the file. Modify the text that you log to console and save changes of `script.js` to see the automatic reload.

#### Local package
Install [lodash](https://lodash.com/) locally and use it to convert 'Foo Bar' to camel case. Modify `script.js` and log the result to console.

## Package.json
* JSON file to define an npm project
* Can contain:
  * Project name, description, version, license etc.
  * Dependencies
  * Required node version (engines)
  * npm scripts (covered later)
  * etc.
  
## Dependencies
* Multiple types of dependencies:
  * dependencies for actual run-time dependencies
  * devDependencies for development-time dependencies such as test frameworks and bundlers
  * peerDependencies for requiring certain versions of other modules to be installed when used (used for example for plugins)
  * optionalDependencies for platform-specific (Windows, OS X, etc.) packages for optimization purposes
* Dependencies can point to npm registry, Git repository, tar ball, local path
* Dependency versions can be specified as specific, greater/lower than, ranges, etc.

## Initializing new project
Run `npm init` and answer all the interactive questions to populate simple package.json

## Installing dependencies
Install all dependencies (dependencies & devDependencies):
``` 
npm install
```

Install only dependencies:
```
npm install --production
```

All dependencies are stored to node_modules folder.

## Adding new dependencies
To add a new dependency for your project, you can use
```
npm install --save express
```
which installs the new package to `node_modules` and adds it to the `package.json`

`--save-dev` to save in `devDepencencies`

Using the dependencies: `const express = require('express');`

## Custom npm scripts
`scripts` field in `package.json` can contain custom scripts
```json
{
    "scripts": {
        "test": "karma run",
        "create-some-folder": "mkdir some && cd some && mkdir other"
    }
}
```

To run these, use:
```
npm run test
npm run create-some-folder
```

Certain scripts (e.g. `start` and `test) are available without the run like`
```
npm start
npm run start
```
### Exercise
* Initialize new project (still in `node` folder) 
* Install lodash as dependency
* Create a custom npm script `start` to `package.json`. The npm script should start `script.js` with `nodemon`. Run the script with `npm start`