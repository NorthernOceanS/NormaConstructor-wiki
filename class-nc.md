# Class `NC` #

`NC` is one of most import class. It have three kinds of API: register API, system API and runtime API.

* constructor
  `new NC()`
* **Register API can only be called before runtime.**
* `nc.registerGenerator(generator)`
  * `generator`: a `Generator`.
  * return value: `undefined`.
* `nc.registerCommandParser(commandParser)`
  * `commandParser`: a command parser.  
  * return value: `undefined`.
* **System API can only be called at runtime.**
  **Normally it is only used by platform, or inner implementation .**
  **If you are a normal developer, please don't rely on these.**
* `nc.createUser()`
  * return value: a `User`.
* `nc.getGenerators()`
  * return value: a array, `Generator[]`.
* **Runtime API can only be called at runtime.**
* `nc.getBlock(c)`
  * `c`: a `Coordinate`.
  * return value: a `Promise`, whose will be resolved a `Block`.
* `nc.setBlock(b)`
  * `b`: a `Block`.
  * return value: a `Promise`, whose will be resolved `undefined`.
* `nc.setTimeout(func, milliseconds)`
  * `func`: a function, which will be called after `milliseconds` milliseconds.
    Because of **tick** exist, the accuracy can hardly exceed a tick.
  * return value: a number.