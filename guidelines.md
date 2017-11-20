# Guidelines, sort of (WORK IN PROGRESS)

An overview of how to use React/Mobx in projects, this is a work in progress that we'll follow while working on the projects.

## Universal

This is used for both front end and back end apps.
Example of a [backend project  (WORK IN PROGRESS)](https://github.com/davorbadrov/api-boilerplate).
Example of a [frontend project (WORK IN PROGRESS)](https://github.com/davorbadrov/frontend-boilerplate)
### Common Backend Packages

- General
    - [hapi](https://github.com/hapijs/hapi) - server
    - [boom](https://github.com/hapijs/boom) - error helper
    - [joi](https://github.com/hapijs/joi) - validation
    - [lodash](https://github.com/lodash/lodash) - utility
    - [uuid](https://github.com/broofa/node-uuid) - Unique ID generation
- Authentication
    - [hapi-auth-jwt2](https://github.com/dwyl/hapi-auth-jwt2)
    - [bcrypt](https://github.com/kelektiv/node.bcrypt.js)
    - [jsonwebtoken](https://github.com/auth0/node-jsonwebtoken)
- Persistence
    - [sequelize](github.com/sequelize/sequelize) - ORM
    - [sequelize-cli](github.com/sequelize/cli) - ORM CLI tool
    - [pg](https://github.com/brianc/node-postgres) - PostgreSQL client
    - [pg-hstore](github.com/scarney81/pg-hstore) - PostgreSQL JSON serializing/deserializing 
- Configuration
    -  [dotenv](https://github.com/motdotla/dotenv)
-  Code quality: testing, linting, formatting
    - [jest](https://github.com/facebook/jest) - test runner
    - [eslint](https://github.com/eslint/eslint) - linter
    - eslint-plugin-import - ESLint ES6 import support
    - eslint-plugin-node - Additional rules for Node
    - eslint-plugin-promise - Enforce best practices for JavaScript promises
    - eslint-config-standard - Enable ESLint standrad.js config
    - eslint-plugin-standard - ESLint Standard.js support
    - [husky](https://github.com/typicode/husky) - Git hooks (used for running formatting
    - lint-staged
    - prettier-standard
- Logging
    - [blipp](https://github.com/danielb2/blipp) - Displays all routes on app start
    - [good](https://www.npmjs.com/package/good) - listens to hapi events and logs them with plugins
    - [good-console](https://github.com/hapijs/good-console) - log good events to console/stdin
    - [good-squeeze](https://github.com/hapijs/good-squeeze) - enables filtering and safe json serialization

## Common Frontend Packages, libs, etc.
- React
- [create-react-app](https://github.com/facebookincubator/create-react-app)
- MobX and MobX-React
- Mobx-React-Form if needed
- Axios
- React-router

## Styleguide

Use [*airbnb*'s styleguide](https://github.com/airbnb/javascript/tree/master/react) ??

### Installation

Dillinger requires [Node.js](https://nodejs.org/) v4+ to run.

Install the dependencies and devDependencies and start the server.

```sh
$ cd dillinger
$ npm install -d
$ node app
```

For production environments...

```sh
$ npm install --production
$ NODE_ENV=production node app
```

License
----

MIT
