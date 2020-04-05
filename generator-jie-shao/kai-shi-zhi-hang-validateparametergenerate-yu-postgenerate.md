# 开始执行——validateParameter,generate与postGenerate

这三个函数会在addon请求开始execute后依次执行。三个函数都没有参数。

validateParameter校验目前参数是否合法。如果你认为可以继续execute，返回`"success"`

在大部分情况下，你只会校验position、blockType与direction是否输入完全。因此下面的代码一般可以用。

```javascript
function () {
                let result = new String()
                if (this.blockTypeArray.indexOf(undefined) != -1)
                    result += "Too few blockTypes!Refusing to execute.\n"
                if (this.positionArray.indexOf(undefined) != -1)
                    result += "Too few positions!Refusing to execute."
                if (result == "") result = "success"

                return result;
            }
```

generate是最重要的函数。它返回一个数组，包含所有需要放置的方块及其位置信息。具体的说，每一个元素都是一个Block：

```text
class Block {
    constructor(position, blockType) {
        this.position = position;
        this.blockType = blockType;
    }
}
```

作为示例，一个典型的添加方块的过程：（来自两点生成）

```javascript
blockArray.push(new Block(
                                new Position(
                                    new Coordinate(x, y, z),
                                    positionArray[0].tickingArea
                                ),
                                blockTypeArray[0])
                            )
```

postGenerate做一些收尾工作，例如清空各个数组、初始化参数等等。

三个函数依次是第12-14个参数。

