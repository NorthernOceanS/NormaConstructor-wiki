# `System`类

`System`是最重要的类。它有两个API：register API, platform used API.

*  构造函数
  `new System()`
* **Register API（只能在运行时之前使用）**
* `system.registerGenerator(generator)`
  * `generator`：一个`Generator`
  * 返回值：`undefined`
* `system.registerCanonicalGenerator(o)`
  * `o`: an argument object.
  * 返回值：`undefined`
* `system.registerCommandParser(commandParser)`
  * `commandParser`：一个命令处理器
  * 返回值：`undefined`
* **platform used API（只能在运行时使用）**
  **此API被用于NormaConstructor框架，如果你是生成器开发者，不建议使用此API。**
* `system.inject(platform)`
  * `platform`: a `Platform`.
  * 返回值：`undefined`
    It's recommended that platform should call
	this function at first line of `use()`.
* `system.createUser(id)`
  * `id`: a number.
  * 返回值：一个`User`
* `system.getUser(id)`
  * `id`: a number.
  * return value: a `User`.
* `system.hasUser(id)`
  * `id`: a number.
  * return value: a boolean.
* **usersystem used API can only be called at runtime.**
  **Normally it is only used by usersystem, or inner implementation.**
  **If you are a normal developer, please don't rely on these.**
* `system.getGenerators()`
  * 返回值：`Generator`数组
* `system.createRuntime(auth)`
  * `auth`: an object represent the authority.
  * return value: a `Runtime`.
