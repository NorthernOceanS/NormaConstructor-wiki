# Event指南 #

Event是NC的一个新概念。

传统上，函数`generate`没有参数，函数`addPosition`有一个`Position`作为参数。然而，这并不适合多用户的情况。所以现在生成器上的每个函数都接收到一个名为`e`的参数。`e`有一些重要的属性。

* `runtime`
  所有的`e`都有一个`runtime`作为属性。`runtime`上有许多所谓的运行时API，比如`logger`。要了解更多，请参见[接口`Runtime`](interface-runtime.md)。
* `state`
  现在，对于每个用户每个生成器，我们都有一个名为`state`的对象。由`e.state`，我们可以访问它们。所有没有被跨生成器和跨用户共享的数据都应该存储在state上。
* `session`
  与`state`不同，`session`是跨生成器的，它与每个用户相关。

一个`e`也有它本应该有的真正参数作为属性，例如，一个`onAddPosition`接收一个带有属性`position`的`e`。
