# Avoid global node modules

Avoid global and try to use locally installed node modules whenever you can, if they are tooling related install them inside dev dependencies via the --dev flag: `npm i --dev package-name`. 

The scripts will now be installed on `npm i`, no need to ask around what the projects global dependencies are, e.g. "How do I run the needed migrations", if the package for migrations is installed locally you'll see the related package listed under dev dependencies. To make it more intuitive add the command as a npm script, they scripts are there to ease up doing repetetive tasks.

E.g. if you use the **sequelize** in your project and **sequelize-cli** for migrations, if the CLI is globally installed you must do:
`sequelize migration:create --name create_user_table`

If the *sequelize-cli* has been added as a dev dependency you can do:
`./node_modules/.bin/sequelize --name create_user_table`

All the packages you might need to interact with are added to the **node_modules/.bin** directory, if you run:
`ls -al node_modules/.bin` inside a node project you'll see a number of the installed packages, all the items you see are symlinks to their corresponding node_module folder.
Npm scripts can directly call the installed tools without specifying the path, so inside package.json you can add a script for creating migrations like:
```json
{
    "name": "npm-local-scripts",
    "version": "0.0.1",
    "scripts": {
        "create-migration": "sequelize migration:create"
    }
}
```

To call it and properly pass the parameters you need to add the `--` flag like this:
`npm run create-migration -- --name create_user_table`

Using this you have to rembemer the `--` flag, but you don't need to remember the exact syntax for the library you might now use very often, e.g. "was it sequelize migration:create or sequelize create:migration". Another advantage of having the script inside package.json is that you can list all the possible commands with `npm run` or even autocomplete the scripts via tab.

## Enable autocompletion of npm script commands

Enabling the commands is pretty straight forward:
```sh
# if you're using zshell
npm completion >> ~/.zshrc # adds the autocompletion code to your rc file
source ~/.zshrc # enable autocompletion by executing the definitions inside the rc file

# if you're using bash
npm completion >> ~/.bashrc
source ~/.bashrc
```
