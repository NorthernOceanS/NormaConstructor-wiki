# Option

在Description中已多次提及Option。这是一个简单的Object。

任何函数都可以修改option：主要是UI，但也可以是add类函数，remove类函数，等等。一个或多个option也可以完全不被修改，虽然没有方法将其显式指定为只读。

有一部分设置是会被addon本身使用的。它们的key会开头带两个下划线。如`"__serverGeneratorIdentifier"`和`"__generateByServer"`（事实上这是目前唯二会被用到的……）因而，建议不要随意设置key开头带双下划线的option，以免产生兼容性问题。（没人会这么干吧……）

这是第5个参数



