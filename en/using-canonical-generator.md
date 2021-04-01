# Using Canonical Generator #

Canonical generator is a kind of generator with certain features. Canonical generators are so common, so that NC have designed a method to register a canonical generator to `system`: `registerCanonicalGenerator`.

**a canonical generator is a generator with fixed number of positions, fixed number of block types and fixed number of directions.**   

**If you want a generator haven't these features, don't use `registerCanonicalGenerator`.**

The `registerCanonicalGenerator` receive an argument object with certain properties, allowing you to control the setting of the generator. See an example of using of `registerCanonicalGenerator`:
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
These properties will be explained following.

* `description`
  * `name`: a string.
    It is a string description what the generator is.
  * `usage`: an object.
    Currently, only `optionUsage` of `usage` is used to set UI.
* `criteria`: an object.
  The three properties of it: `positionsLength`, `blockTypesLength` and `directionsLength` are used to set the number of positions, of block types and of directions.
* `method`
  * `generate`
  * `UIhandle`
  See [Guide for Event](guide-for-event.md).
