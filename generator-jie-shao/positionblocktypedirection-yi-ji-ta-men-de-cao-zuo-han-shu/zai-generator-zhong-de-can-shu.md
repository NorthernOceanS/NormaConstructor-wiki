# 在generator中的参数

## positionArray,blockTypeArray,directionArray

这三个数组分别保存刚刚提到的三类数据，它们会在运行generate函数时用到。（但它们并不是generate函数的参数，它并没有参数。）

这三个数组被建入generator，而非为各个generator共享的原因原本是为了切换generator时，原先生成器的数据保留，使得玩家可以从上次中断的位置继续。但需要时，也可以适应不同生成器的需求（有限/不限长度数据量，预设数据，等等）

## add类函数（addPosition,addBlockType,addDirection）

add类函数仅有一个参数，忽略其返回值。传入参数即各自类型的结构体，这个函数应将其保存入各自的数组。

## remove类函数（removePosition,removeBlockType,removeDirection）

remove类函数也只有一个参数，忽略其返回值。传入参数是一个index，这个函数应移除对应位置的数组元素。

## ……晕了？

呃……我会分享一份我的代码。如果在你的设计中，三类数据都应当拥有固定的长度，（意即，每次三个数组都应该写入固定数量的数据量）下面的代码可以用。（以position为例。你会需要预先把positionArray设置为一个相应长度的、全都是`undefined`的数组）

```javascript
function (position) {
                displayObject(position)
                let indexOfVacancy = this.positionArray.indexOf(undefined)
                if (indexOfVacancy == -1) displayChat("Too many positions!New one is ignored")
                else this.positionArray[indexOfVacancy] = position
            }
```

```javascript
function (index) {
                if (index === undefined)
                    for (index = this.positionArray.length - 1; index >= 0 && this.positionArray[index] == undefined; index--);
                if (index >= 0) this.positionArray[index] = undefined
                displayObject(this.positionArray)
            }
```

各数组以及对应的操作函数对应第2-4、6-11个参数。

