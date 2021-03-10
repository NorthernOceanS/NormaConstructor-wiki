# 自定义生成器 #

您可以使用`system.registercanonicalgenerator()`注册一个标准生成器。但是，如果您想要标准生成器以外的功能，您可以自定义生成器。
`Generator`是一个带有若干个函数的对象，所以任何带有这些函数的对象都可以注册为`Generator`。


```JS
// in plugin/my-generator/index.js
import system from '../../system.js';

system.registerGenerator({
    name: Symbol("generator-name"),
    onInit(e) {
        e.state.positions = [];
    },
    onAddPosition(e) {
        e.state.positions.push(e.position);
    },
    onAddBlockType(e) { /* no-op */ },
    onAddDirection(e) { /* no-op */ },
    onRemovePoistion(e) { /* no-op */ },
    onRemoveBlockType(e) { /* no-op */ },
    onRemoveDirection(e) { /* no-op */ },
    isValidParameter(e) { /* no-op */ },
    generate(e) { /* no-op */ },
    onExit(e) { /* no-op */ },
});

```
实际上，`system.registerCanonicalGenerator(o)`指向`system.registerGenerator(canonicalGeneratorFactory(o))`。

    译者：英文文档未提供更多内容。
