# 使用经典生成器

经典生成器是一种具有一定特征的生成器。经典生成器非常常见，因此NC设计了一种方法来将经典生成器注册到system: `registerCanonicalGenerator`。

**一个经典生成器是一个具有固定数量的位置、固定数量的方块类型和固定数量的方向的生成器。**

** 如果你想要一个没有这些特性的生成器，不要使用`registerCanonicalGenerator`**

`registerCanonicalGenerator`接收一个具有特定属性的对象，允许您控制生成器的设置。参见`registerCanonicalGenerator `的一个使用示例:
```JS
system.registerCanonicalGenerator({
    description: {
        name: "example generator",
        usage: {
            positionUsage: [],
            blockTypeUsage: [],
            directionUsage: [],
            optionUsage: []
        }
    },
    criteria: {
        positionsLength: 0,
        blockTypesLength: 0,
        directionsLength: 0,
    },
    method: {
        generate: function (e) {
            return [];
            // the Generator can not actually generate anything,
            // but it can be a example of how to register a generator.
        }
    }
});
```
这些属性将被解释如下。

* `description`
  * `name`: 一个string。
    它是一个描述生成器是什么的字符串。
  * `usage`: 一个object。
    目前，只有`usage`中的`optionUsage`被使用，用于设置UI。
* `criteria` : 一个object。
  它的三个属性: `positionsLength`,`blockTypesLength`和`directionsLength`用于设置位置、方块类型和方向的数量。
* `method`
  * `generate`
  * `UIhandle`
  参见[Event指引](guide-for-event.md)。
