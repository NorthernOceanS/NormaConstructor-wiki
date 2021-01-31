# Class `System` #

`System` is one of most import class. It have two kinds of API: register API, system API.

* constructor
  `new System()`
* **Register API can only be called before runtime.**
* `system.registerGenerator(generator)`
  * `generator`: a `Generator`.
  * return value: `undefined`.
* `system.registerCommandParser(commandParser)`
  * `commandParser`: a command parser.  
  * return value: `undefined`.
* **platform used API can only be called at runtime.**
  **Normally it is only used by platform, or inner implementation .**
  **If you are a normal developer, please don't rely on these.**
* `system.createUser()`
  * return value: a `User`.
* `system.getGenerators()`
  * return value: a array, `Generator[]`.
