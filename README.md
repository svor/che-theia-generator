# @eclipse-che/theia-generator
===================================


# Installation guide

Theia Generator can be installed locally or globally

Here is how to install it globally:

using yarn:
```
$ yarn global add @eclipse-che/theia-generator
```

using npm:
```
$ npm install -g @eclipse-che/theia-generator
```

Then, a new command line tool is available : `che:theia`

# Using the tool

Once the tool is installed, the following commands are available:
- `che:theia init`
- `che:theia production`

(help is also available with command `che:theia --help`)

## che:theia init

This command needs to be launched inside a cloned directory of Eclipse Theia cloned directory

```
$ git clone https://github.com/theia-ide/theia
$ cd theia
$ che:theia init
```

once the init command has been launched:
- inside `theia/che` folder, all extensions have been cloned and checkout to their correct branches (if specified)
- all extensions have their package.json updated to the versions used by the current theia. (cloned)
- in `packages` folder, there are symlinks for each extension coming from `theia/che` folders. All packages are prefixed by `@che-`
- in `examples` folder, a new folder named àssembly` has been generated and include the `che-theia` assembly of Theia

In order to build the product, just run `yarn` at the root folder (where theia has been cloned)

### Custom extension set

Also you can provide custom `yaml` with your extension set, by using `-c` or `--config` parameter of `che:theia init` :

`che:theia init -c ./path/to/custom/extensions.yaml`

The sample of `extensions.yaml` can be found [there](./src/conf/extensions.yml)

### Dev mode

Dev mode is the way to use all new extensions from `master` branch:

`che:theia init -d`

And `che:theia` will use `master` branch for all extensions, regardless of provided configuration

### Development life-cycle
it's easy to check changes. Running yarn watch in a module and then running yarn watch in `examples/assembly` folder and using `yarn run start` in `examples/assembly`


## che:theia production
A production's ready assembly of che-theia can be obtained by running from the root folder of theia: `che:theia production`

It will generate in `${where theia has been cloned}/production` folder a ready-to-use assembly of theia, without lot of files (like source maps, source code, etc)

It can be started with the command `node ${where theia has been cloned}/production/src-gen/backend/main.js`

## che:theia clean

If you want to clean up your Theia repository use
`che:theia clean` command, and it will undo all modification on your repository

# Developer's guide
[See Contributing](CONTRIBUTING.md)

# License

[EPL-2.0](LICENSE)
