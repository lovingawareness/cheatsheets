# node cheatsheet

1. `npm install` - After cloning a repository of a Node.js project (like [this one](https://github.com/tothebeat/emergency-compliment)), run `npm install` to install the required packages. This information comes from the `package.json` file in the root folder of the project.
1. `npm init` - This starts a Node.js project in the current folder. This creates a `package.json` configuration file, and starts a wizard to fill out some identifying information on you as the author and the project itself.
1. `npm install <packagename>` - This installs a package from the [npmjs.com](https://www.npmjs.com/) package index, and saves the package name and version number to the `package.json` file (under `"dependencies"`) in the current directory.
1. `npm search <package-search-query>` - Like if I want to search for packages with `munkres` in the name, I can do `npm search munkres` and get:

   ```
    NAME                      | DESCRIPTION          | AUTHOR          | DATE       | VERSION  | KEYWORDS
    munkres-js                | Munkres (aka…        | =addaleax       | 2017-01-02 | 1.2.2    | assignment munkres hungarian
    hungarian-on3             | A hungarian…         | =mattkrick      | 2015-09-19 | 0.3.1    | Hungarian Munkres Kuhn assignment problem bipartite
    moresketchy               | A linted fork of…    | =wbern          | 2017-04-18 | 1.0.6    | sketchy shapecompare compare shapes 2d hungarian munkres
   ```

1. `npm install <packagename> --save-dev` - This installs the package in the current project folder, but also saves the package name and version in `package.json` in a different area (under `"devDependencies"`).
1. `npm install how-to-npm -g && how-to-npm` - Gets you started with [an interactive tutorial](https://www.npmjs.com/package/how-to-npm) at the command line for npm and setting up a development environment.

## References:

1. [MDN's Setting up a Node development environment](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/development_environment)
1. [npm official reference on package.json config file](https://docs.npmjs.com/files/package.json)
1. [package.json: An Interactive Guide](http://browsenpm.org/package.json)
1. [npmjs.com official package index](https://www.npmjs.com/)
1. [The Anatomy of A Modern JavaScript Application](https://www.sitepoint.com/anatomy-of-a-modern-javascript-application/)
1. [Server-side Programming and Node - Daniel Shiffman](http://shiffman.net/a2z/server-node/)
1. [Learning JavaScript Design Patterns](https://addyosmani.com/resources/essentialjsdesignpatterns/book/)
1. [Patterns For Large-Scale JavaScript Application Architecture](https://addyosmani.com/largescalejavascript/)
1. [Deploying Node.js Apps on Heroku](https://devcenter.heroku.com/articles/deploying-nodejs)

### Tutorials

1. [Teach Yourself Node.js in 10 Steps](https://ponyfoo.com/articles/teach-yourself-nodejs-in-10-steps)
1. [Awesome Node.js](https://github.com/sindresorhus/awesome-nodejs/blob/master/readme.md)
