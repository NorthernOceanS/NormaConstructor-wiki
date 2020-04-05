# position,blockType,direction,以及他们的操作函数

## Position

```javascript
class Coordinate {
    constructor(x, y, z) {
        this.x = x;
        this.y = y;
        this.z = z;
    }
}
class Position {
    constructor(coordinate, tickingArea) {
        this.coordinate = coordinate;
        this.tickingArea = tickingArea;
    }
}

```

Position是一个复合的结构体，第一个结构体是Coordinate，表示坐标。第二个是tickingArea。

## BlockType

```javascript
class BlockType {
    constructor(blockIdentifier, blockState) {
        this.blockIdentifier = blockIdentifier;
        this.blockState = blockState;
    }
}
```

BlockType描述方块类型。blockIdentifier是方块名，而blockState是minecraft中block的component，描述方块的额外信息。（比如，混凝土的颜色）

## Direction

```javascript
class Direction {
    constructor(x, y) {
        this.x = x;
        this.y = y;
    }
}
```

这在minecraft中的标准名称是rotation……表示玩家的朝向。

