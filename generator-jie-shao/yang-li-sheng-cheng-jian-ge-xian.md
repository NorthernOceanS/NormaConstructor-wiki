# 样例：生成间隔线

```javascript
(function () {
    generatorArray.push(
        new Generator(
            new Description("Create a line with given interval.",
                new Usage(
                    ["Start point"],
                    ["BlockType"],
                    ["Direction"],
                    [
                        {
                            viewtype: "edittext",
                            text: "Length:",
                            key: "length",
                        },
                        {
                            viewtype: "edittext",
                            text: "Interval:",
                            key: "interval",
                        }
                    ])
            ),

            [undefined],
            [undefined],
            [undefined],
            {
                "positionArrayLengthRequired": 1,
                "blockTypeArrayLengthRequired": 1,
                "directionArrayLengthRequired": 1,
                "length": 0,
                "interval": 0
            },

            function (position) {
                displayObject(position)
                let indexOfVacancy = this.positionArray.indexOf(undefined)
                if (indexOfVacancy == -1) displayChat("Too many positions!New one is ignored")
                else this.positionArray[indexOfVacancy] = position
            },
            function (blockType) {
                displayObject(blockType)
                let indexOfVacancy = this.blockTypeArray.indexOf(undefined)
                if (indexOfVacancy == -1) displayChat("Too many blockTypes!New one is ignored")
                else this.blockTypeArray[indexOfVacancy] = blockType
            },
            function (direction) {
                displayObject(direction)
                let indexOfVacancy = this.directionArray.indexOf(undefined)
                if (indexOfVacancy == -1) displayChat("Too many directions!New one is ignored")
                else this.directionArray[indexOfVacancy] = direction
            },
            function (index) {
                if (index === undefined)
                    for (index = this.positionArray.length - 1; index >= 0 && this.positionArray[index] == undefined; index--);
                if (index >= 0) this.positionArray[index] = undefined
                displayObject(this.positionArray)
            },
            function (index) {
                if (index === undefined)
                    for (index = this.blockTypeArray.length - 1; index >= 0 && this.blockTypeArray[index] == undefined; index--);
                if (index >= 0) this.blockTypeArray[index] = undefined
                displayObject(this.blockTypeArray)
            },
            function (index) {
                if (index === undefined)
                    for (index = this.directionArray.length - 1; index >= 0 && this.directionArray[index] == undefined; index--);
                if (index >= 0) this.directionArray[index] = undefined
                displayObject(this.directionArray)
            },

            function () {
                let result = new String()
                if (this.blockTypeArray.indexOf(undefined) != -1)
                    result += "Too few blockTypes!Refusing to execute.\n"
                if (this.positionArray.indexOf(undefined) != -1)
                    result += "Too few positions!Refusing to execute."
                if (this.directionArray.indexOf(undefined) != -1)
                    result += "Too few directions!Refusing to execute."
                if (result == "") result = "success"

                return result;
            },
            function () {
                let blockArray = []

                displayChat("§b NZ is JULAO!")

                let positionArray = this.positionArray
                let blockTypeArray = this.blockTypeArray
                let directionArray = this.directionArray

                displayChat("§b Yes, NZ is JULAO!")


                let direction = (function () {
                    if (-45 <= directionArray[0].y && directionArray[0].y <= 45) return "+z"
                    else if (-135 <= directionArray[0].y && directionArray[0].y <= -45) return "+x"
                    else if (45 <= directionArray[0].y && directionArray[0].y <= 135) return "-x"
                    else return "-z"
                }());

                switch (direction) {
                    case "+z": {
                        let x = positionArray[0].coordinate.x
                        let y = positionArray[0].coordinate.y
                        for (let z = positionArray[0].coordinate.z; z < this.option.length + positionArray[0].coordinate.z; z += (this.option.interval + 1))
                            blockArray.push(new Block(
                                new Position(
                                    new Coordinate(x, y, z),
                                    positionArray[0].tickingArea
                                ),
                                blockTypeArray[0])
                            )
                        break;
                    }
                    case "-z": {
                        let x = positionArray[0].coordinate.x
                        let y = positionArray[0].coordinate.y
                        for (let z = positionArray[0].coordinate.z; z > -this.option.length + positionArray[0].coordinate.z; z -= (this.option.interval + 1))
                            blockArray.push(new Block(
                                new Position(
                                    new Coordinate(x, y, z),
                                    positionArray[0].tickingArea
                                ),
                                blockTypeArray[0])
                            )
                        break;
                    }
                    case "+x": {
                        let z = positionArray[0].coordinate.z
                        let y = positionArray[0].coordinate.y
                        for (let x = positionArray[0].coordinate.x; x < this.option.length + positionArray[0].coordinate.x; x += (this.option.interval + 1))
                            blockArray.push(new Block(
                                new Position(
                                    new Coordinate(x, y, z),
                                    positionArray[0].tickingArea
                                ),
                                blockTypeArray[0])
                            )
                        break;
                    }
                    case "-x": {
                        let z = positionArray[0].coordinate.z
                        let y = positionArray[0].coordinate.y
                        for (let x = positionArray[0].coordinate.x; x > -this.option.length + positionArray[0].coordinate.z; x -= (this.option.interval + 1))
                            blockArray.push(new Block(
                                new Position(
                                    new Coordinate(x, y, z),
                                    positionArray[0].tickingArea
                                ),
                                blockTypeArray[0])
                            )
                        break;
                    }
                }

                return blockArray
            },
            function () {
                this.positionArray = [undefined]
                this.blockTypeArray = [undefined]
                this.directionArray = [undefined]
            }
        )
    )
}());
```

……好吧写的不是最好。

