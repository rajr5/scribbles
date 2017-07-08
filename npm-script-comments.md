# Tips for using npm scripts

## Avoiding global packages

Instead of using global packages try using locally installed ones where it makes sense, especially for dev dependencies. When using tools like `sequelize` it's better to install both `sequelize` and the `sequelize-cli` locally.

This will:
- prevent version mismatches with your coworkers
- make the tooling for the project the projects dependency as it should be
- less setting up when starting to work on the project

```sh
# use 
npm i --dev sequelize sequelize-cli

# instead of 
npm i -g sequelize sequelize-cli
```


### Passing params to those scripts
You can pass params to npm scripts by passing the `--` flag
When using globally installed _sequelize-cli_ you'd write:

```sh
sequelize migration:create --name add_user_table
```

by using locally installed package you can use

```sh
npm run migration:create -- --name add_user_table
```

### Commenting the npm scripts

The comments for npm scripts aren't supported by default, the JSON format doesn't allow for comments by default, but there are a few hacks that can be used.

Let's assume we have a `package.json`:
```json
{
    "name": "npm-script-tips",
    "version": "0.0.1",
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1",
        "build": "echo \"Building static assets\""
    }
}
```

To check the available scripts we can run `npm run` in a shell, and we get the list of all available scripts:
```
→ npm run
Lifecycle scripts included in npm-script-tips:
  test
    echo "Error: no test specified" && exit 1

available via `npm run-script`:
  build
    echo "Building static assets"
```

To add a comment you can add fake a script like the following:
```
{
    "name": "npm-script-tips",
    "version": "0.0.2",
    "scripts": {
        "//test": "This will run the app's tests",
        "test": "echo \"Error: no test specified\" && exit 1",
        "//build": "This will build the static assets",
        "build": "echo \"Building static assets\""
    }
}
```

The output after `npm run` is now a bit better:
```
→ npm run
Lifecycle scripts included in npm-script-tips:
  test
    echo "Error: no test specified" && exit 1

available via `npm run-script`:
  //test
    This will run the app's tests
  //build
    This will build the static assets
  build
    echo "Building static assets"
```
But now we don't have the comment and the script grouped together. Watching [egghead.io's](https://egghead.io/instructors/elijah-manor) tutorials on npm scripts a great solution has been proposed by [Elijah Manor](http://elijahmanor.com) where he suggests using the following trick:
```json
{
    "name": "npm-script-tips",
    "version": "0.0.3",
    "scripts": {
        "test": "# This will run the tests \n\t echo \"Error: no test specified\" && exit 1",
        "build": "# This will build the static assets \n\t echo \"Building static assets\""
    }
}
```
The output looks great with this trick:
```
→ npm run
Lifecycle scripts included in npm-script-tips:
  test
    # This will run the tests
	 echo "Error: no test specified" && exit 1

available via `npm run-script`:
  build
    # This will build the static assets
	 echo "Building static assets"
```

Most of egghead's tutorials are for subscribers only but they definitely pay out to have and their videos usually take only a few minutes.
