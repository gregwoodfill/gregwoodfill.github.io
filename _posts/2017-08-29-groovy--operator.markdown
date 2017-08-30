---
layout: post
title: "Groovy @ Operator"
date: "2017-08-29 19:03:52 -0500"
---
In Groovy there are times you need to bypass the implicit calls to a getter or setter when calling.
```
class Foo {
  String a = "bar"

  String getA() {
    "foobar"
  }
}
```
You can bypass this by calling
object.@property
e.g.
`foo.@a == "bar"`
