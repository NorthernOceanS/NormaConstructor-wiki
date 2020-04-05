# generator介绍



在NormaConstructor，每一种功能（如“两点生成”、“复制粘贴”）背后都是一个"generator"。一个generator保存四类数据：

* position:位置信息
* blockType:方块种类
* direction:\(玩家\)朝向信息
* option:generator自设的更多数据\(例如"造马路"中，指定长度和马路类型等\)

保存这四个数据后，generate函数会根据这些数据生成一份blockArray——顾名思义，里面全都是block（之后会提到block这一数据体）。这一block发送至server，由server生成。

（不少事情是只有server的脚本能做的，比如放置方块不能由client执行。）

……如果上面这些没有把你绕晕，那么你可以迎接下面这个：

```javascript
class Generator {
    constructor(description,
        positionArray, blockTypeArray, directionArray, option,
        addPosition, addBlockType, addDirection,
        removePosition, removeBlockType, removeDirection,
        validateParameter, generate, postGenerate) {
        /*一堆代码*/
    }
}
```

这便是generator的原型。每次添加一个新功能，你需要：

* new一个generator，
* 填入所有参数，
* 将其push入generatorArray

（可能需要注意的是，generatorArray里的各个generator是**独立**的，你的代码中不应该依赖于某个generator的index，因为这很可能改变。）

我的做法是利用js的[立即调用函数表达式](https://developer.mozilla.org/zh-CN/docs/Glossary/%E7%AB%8B%E5%8D%B3%E6%89%A7%E8%A1%8C%E5%87%BD%E6%95%B0%E8%A1%A8%E8%BE%BE%E5%BC%8F)：

```javascript
(function(){
    generatorArray.push(new Generator(
        /*14个参数*/
    ))
}())
```

将其写在client.js的最后。~~（方便折叠）~~

现在，我将依次介绍这些参数。

