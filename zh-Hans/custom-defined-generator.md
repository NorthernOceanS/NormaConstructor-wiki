# Custom Defined Generator #

You already can use `system.registerCanonicalGenerator()` to register a canonical Generator to system. However, if you want freedom other than canonical Generator, you can define your own Generator.
`Generator` is a object with a couple of functions, so any object with such functions can be registered as `Generator`.


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
Actually, `system.registerCanonicalGenerator(o)` is a shorthand of `system.registerGenerator(canonicalGeneratorFactory(o))`.