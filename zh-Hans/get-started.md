# 开始 #

## 安装 ##
此项目需要nodeJS，如果你没有nodeJS，请[安装](https://nodejs.org/)。  
现在，请使用GIT克隆我们的项目。

在终端执行：
```shell
$ git clone https://github.com/NorthernOceanS/NormaConstructor-template.git
$ # Just a sample, there is no such project
$ cd NormaConstructor-template
$ npm insall
```

## Hello World ##
这是文件的结构，要编写一个新的生成器，你需要在`/packs/behaviors/scripts/plugin/`创建一个文件夹，而项目的入口是`index.js`。
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
更多信息请参见 [**参考**](reference.md)。


## 插件的位置

所有的插件都被应该封装在一个文件夹中，放在`/packs/behaviors/scripts/plugin/`。`index.js`为入口。
* plugin
  * hello
    * index.js 
  * ...

## `system` API ##
`system` 是一个全局唯一的对象。

### 注册 API ###
`system.registerGenerator()`可以用来注册生成器。（常用）

`system.registercommandparser()`可以注册一个命令解析器。

更多信息请参见 [**参考**](reference.md) 。

### 平台 API ###
**Runtime API 只能在运行时中使用**

`runtime`将在运行时中提供像`runtime.getblock()`这样的 API 。

更多信息请参见 [**参考**](reference.md) 。

## 脚本 ##
此项目使用了[minecraft-addon-toolchain](https://minecraft-addon-tools.github.io/)，
所以可以使用

```shell
$ npm run build
$ npm run watch
$ npm run installaddon
$ npm run uninstalladdon
$ npm run packageaddon
```
你可以
使用 `npm run build` 来创建一个 mcaddon 的结构，
使用 `npm run installaddon` 安装 Win 10 的插件，
使用 `npm run uninstalladdon` 卸载 Win 10 的插件，
使用 `npm run packageaddon` 创建一个 mcaddon 包，
以此类推。
