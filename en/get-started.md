# Get Started #

## Installation ##
NormaConstructor requires nodejs, if you haven't install nodejs, install [it](https://nodejs.org/) first.
Now you can clone the repository.

```shell
$ git clone https://github.com/NorthernOceanS/NormaConstructor-template.git
$ # Just a sample, there is no such project
$ cd NormaConstructor-template
$ npm insall
```

## Hello World ##
The project have a structure like this, and to write a new `Generator`, all you need to do is creating a folder with a  file `index.js` in `packs/behaviors/scripts/plugin/`.
.

  * packs 
    * behaviors
      * scripts
        * client
          * index.js
        * system.js
        * plugin
          * hello
            * index.js
          * ...
        * ...
    * resources
    * ...

```JS
// in plugin/hello/index.js
import system from '../../system.js';

system.registerCanonicalGenerator({
    name: "hello world",
    criteria: {
        positionsLength: 0,
        blockTypesLength: 0,
        directionsLength: 0,
    },
    method: {
        generate: function (e) {
            return;
            // the Generator can not actually generate anything,
            // but it can be a sample of how to register a generator.
        }
    }
});
```
To read more, see [**reference**](reference.md).


##  plugin location

All plugins are enclosed by a folder and placed inside the `plugin` folder. An `index.js` must be present.
* plugin
  * hello
    * index.js 
  * ...

## `system` API ##
`system` is a global unique object.

### Register API ###
`system.registerGenerator()` is the most useful API. It can be used to register `Generator`s  to the system. 

`system.registerCommandParser()` is an API which can register a command parser to system.

To read more, see [**reference**](reference.md).

### Platform API ###
**Runtime API can only used in runtime.**

The runtime will provide API like `runtime.getBlock()` in runtime.

To read more, see [**reference**](reference.md).

## Scripts ##
The project use [minecraft-addon-toolchain](https://minecraft-addon-tools.github.io/
) as its dependence, so it can use scripts

```shell
$ npm run build
$ npm run watch
$ npm run installaddon
$ npm run uninstalladdon
$ npm run packageaddon
```
You can
use `npm run build` to create the structure of a mcaddon,
use `npm run installaddon` to install the addon for Win10,
use `npm run uninstalladdon` to uninstall the addon for Win10,
use `npm run packageaddon` to create a mcaddon package,
or do other things you want.