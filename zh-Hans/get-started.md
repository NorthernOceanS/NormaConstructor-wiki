# 开始 #

## 安装 ##
NormaConstructor 需要 nodejs ，如果你还没有安装 nodejs ，请先安装[它](https://nodejs.org/)。
现在可以克隆库了。

```shell
$ git clone https://github.com/NorthernOceanS/NormaConstructor-template.git
$ # Just a sample, there is no such project
$ cd NormaConstructor-template
$ npm insall
```

## Hello World ##
这个项目的结构像是这样，要编写一个新的“生成器”，你所需要做的就是在 `packs/behaviors/scripts/plugin/` 下创建一个带有文件 `index.js` 的文件夹。
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
更多信息请参见 [**参考**](reference.md) 。


## 插件的位置

所有的插件都被应该封装在一个文件夹中，放在 `plugin` 文件夹中。一个 `index.js` 必须存在。
* plugin
  * hello
    * index.js 
  * ...

## `system` API ##
`system` 是一个全局唯一的对象。

### 注册 API ###
`system.registerGenerator()` 是最有用的 API 。它可以用来注册生成器到系统。

`system.registercommandparser()` 是一个 API ，它可以注册一个命令解析器到系统。

更多信息请参见 [**参考**](reference.md) 。

### 平台 API ###
**运行时 API 只能在运行时中使用**

`runtime`将在运行时中提供像`runtime.getblock()`这样的 API 。

更多信息请参见 [**参考**](reference.md) 。

## 脚本 ##
此项目使用[minecraft-addon-toolchain](https://minecraft-addon-tools.github.io/
)作为它的依赖，所以它可以使用脚本

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
或者做其他你想做的事。