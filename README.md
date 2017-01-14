# eslint-config-lionel-lints

[![License][license-img]][license-url]

Lionel Lints's fork of Ryan Sobol's shareable ESLint configuration. This fork is being cut to experiment with different rules and styleguides while maintaining the overall linting philosophy set out by the original repo.

## Philosophy

A major aspect of the [ESLint philosophy](eslint_philosophy) is that it doesn't promote any particular coding style. While there are many different styles of writing JavaScript, the ESLint rules in this shareable configuration adhere the following philosophy.

- Declare all available rules
- Support ECMAScript 5 and above
- Be compatible with alternative parsers
- Break the build when code fails any rule
- Equip developers with powerful semantics
- Teach developers how to write maintainable code
- Allow any rule to be overridden on a per project basis

## Dependencies

| Dependency                   | Type     | Version              |
|------------------------------|----------|----------------------|
| [eslint][eslint]             | Peer     | `^3.10.2`            |
| [eslint-plugin-react][react] | Required | `^6.7.1`             |
| [node][node]                 | Engine   | `^4.2.0 || >= 6.0.0` |

## Global usage

Install the package globally.

```shell
npm install -g eslint eslint-config-lionel-lints
```

Change into your project's directory.

```shell
cd path/to/project
```

Create a `.eslintrc.js` configuration file.

```shell
touch .eslintrc.js
```

Add [language configuration][language] and [environment configuration][environment] to the `.eslintrc.js` file.

```js
module.exports = {
  extends: [
    'lionel-lints/browser',
    'lionel-lints/es6'
  ]
};
```

Run `eslint` globally and fix any linting errors.

```shell
eslint .
```

## Local usage

Change into your project's directory.

```shell
cd path/to/project
```

If you haven't already, create a `package.json` file.

```shell
npm init
```

Install the package locally and add it to the `package.json` file as a development dependency.

```shell
npm install -D eslint eslint-config-lionel-lints
```

Create a `.eslintrc.js` configuration file.

```shell
touch .eslintrc.js
```

Add [language configuration][language] and [environmnent configuration][environment] to the `.eslintrc.js` file.

```js
module.exports = {
  extends: [
    'lionel-lints/browser',
    'lionel-lints/es6'
  ]
};
```

Run `eslint` locally and fix any linting errors.

```shell
./node_modules/.bin/eslint .
```

Additionally, add a script to the `package.json` file.

```json
{
  "script": {
    "lint": "eslint"
  }
}
```

Then run the `npm` script and fix any linting errors.

```shell
npm run lint .
```

## Language configuration

A project is linted by **one** of the following language configurations.

| Language     | Module               |
|--------------|----------------------|
| ECMAScript 5 | `lionel-lints/es5`   |
| ECMAScript 6 | `lionel-lints/es6`   |
| ECMAScript 7 | `lionel-lints/es7`   |
| ECMAScript 8 | `lionel-lints/es8`   |

Add the following code to the `.eslintrc.js` file of an ECMAScript 6 project.

```js
module.exports = {
  extends: 'lionel-lints/es6'
};
```

Or add the following code to the `.eslintrc.js` file of an ECMAScript 7 project.

```js
module.exports = {
  extends: 'lionel-lints/es7'
};
```

## Overriding rules

Customize any rule by overriding it in the `.eslintrc.js` file.

```js
module.exports = {
  extends: 'lionel-lints/es6',

  rules: {
    'brace-style': [2, '1tbs', { allowSingleLine: true }],
  }
};
```

## Environment configuration

Additionally, a project is linted by **any** of the following environment configurations.

| Environment | Module                     |
|-------------|----------------------------|
| browser     | `lionel-lints/browser`     |
| Express     | `lionel-lints/express`     |
| jQuery      | `lionel-lints/jquery`      |
| Materialize | `lionel-lints/materialize` |
| Mocha       | `lionel-lints/mocha`       |
| Node.js     | `lionel-lints/node`        |
| React       | `lionel-lints/react`       |

Add the following code to the `.eslintrc.js` file of an ECMAScript 6 project that's running in a browser.

```js
module.exports = {
  extends: [
    'lionel-lints/browser',
    'lionel-lints/es6'
  ]
};
```

Add the following code to the `.eslintrc.js` file of an ECMAScript 6 project that's running in a browser and using jQuery.

```js
module.exports = {
  extends: [
    'lionel-lints/browser',
    'lionel-lints/es6',
    'lionel-lints/jquery'
  ]
};
```

Add the following code to the `.eslintrc.js` file of an ECMAScript 6 project that's running in Node.js.

```js
module.exports = {
  extends: [
    'lionel-lints/es6',
    'lionel-lints/node'
  ]
};
```

Add the following code to the `.eslintrc.js` file of an ECMAScript 6 project that's running in both a browser and Node.js as well as using React.

```js
module.exports = {
  extends: [
    'lionel-lints/browser',
    'lionel-lints/es6',
    'lionel-lints/node',
    'lionel-lints/react'
  ]
};
```

**NOTE:** To include `.jsx` files in the linting, use the `eslint . --ext .js,.jsx` command.

## Parsers options

Parser options, like support for ECMAScript 6 modules, can be specified in the `.eslintrc.js` file.

```js
module.exports = {
  extends: [
    'lionel-lints/browser',
    'lionel-lints/es6',
    'lionel-lints/node',
    'lionel-lints/react'
  ],

  parserOptions: {
    sourceType: 'module'
  }
};
```

## Alternative parsers

The default parser is [Espree][espree] but alternative parsers, like [babel-eslint][babel], can be specified in the `.eslintrc.js` file.

```js
module.exports = {
  extends: [
    'lionel-lints/browser',
    'lionel-lints/es6',
    'lionel-lints/node',
    'lionel-lints/react'
  ],

  parser: 'babel-eslint'
};
```

## ESLint environments

Additional [ESLint environments][env], like `worker`, can also be specified in the `.eslintrc.js` file.

```js
module.exports = {
  env: {
    worker: true
  },

  extends: [
    'lionel-lints/browser',
    'lionel-lints/es6',
    'lionel-lints/node',
    'lionel-lints/react'
  ]
};
```

## Contributing

If you want to customize any of the rules for your own project, see the section on [overriding rules][overriding] to learn how.

Pull requests are very much welcome for the following.

- Fixing bugs
- Adding tests
- Writing documentation
- Adding rules for another plugin (e.g. [eslint-plugin-angular][angular])
- Changing rules that don't follow the [project's philosophy][philosophy]

## Credits

Thanks to the Shopify team for publishing [eslint-config-shopify][shopify] under a permissive license.

Also, thanks to my colleagues and students at [Galvanize][galvanize] for helping me with testing.

A final thanks to Ryan for setting up an awesome linting walkthrough that I can build on.

[license-img]: https://img.shields.io/npm/l/eslint-config-lionel-lints.svg?style=flat-square
[license-url]: https://github.com/lionel-lints/eslint-config-lionel-lints/blob/master/LICENSE

[angular]: https://github.com/Gillespie59/eslint-plugin-angular
[babel]: https://github.com/babel/babel-eslint
[env]: http://eslint.org/docs/user-guide/configuring#specifying-environments
[eslint]: http://eslint.org/
[eslint_philosophy]: http://eslint.org/docs/about/
[espree]: https://github.com/eslint/espree
[galvanize]: http://www.galvanize.com/
[node]: https://nodejs.org/
[react]: https://github.com/yannickcr/eslint-plugin-react
[shopify]: https://github.com/Shopify/eslint-config-shopify
[language]: #language-configuration
[overriding]: #overriding-rules
[philosophy]: #philosophy
[environment]: #environment-configuration
