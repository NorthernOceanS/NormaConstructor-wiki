#`System`类#

`System`是最重要的类。它有两个API：register API, platform used API.

##构造函数
`new System()`

###Register API只能在运行时之前使用
####`system.registerGenerator(generator)`

`generator`：一个`Generator`
返回值：`undefined`

####`system.registerCommandParser(commandParser)`
`commandParser`：一个命令处理器
返回值：`undefined`

###platform used API只能在运行时使用
此API被用于NormaConstructor框架，如果你是生成器开发者，不建议使用此API。

####`system.createUser()`
返回值：一个`User`

####`system.getGenerators()`
返回值：`Generator`数组
