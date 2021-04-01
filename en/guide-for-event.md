# Guide for Event #

Event is a new concept of NC.

Traditionally, function `generate` have no arguments, function `addPosition` has a `Position` as its argument. However, This is shown not fit multi-user situation. So now every function on generator receive an argument named `e`. And the `e` have some import properties on it.

* `runtime`
  All `e` have a `runtime` as property. The `runtime` have many so called runtime API as `logger`. To know more, see [Interface `Runtime`](interface-runtime.md).
* `state`
  Now we have an object called `state` for every user every generator. By `e.state`, we can access to them. All data not shared cross generate and cross user should be stored on `state`.
* `session`
  Instead of `state`, `session` is cross generator, it's related to each user.

An `e` also have the real argument it should have as property, for example, a `onAddPosition` receive an `e` with property `position`.
