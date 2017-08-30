---
layout: post
title: Kotlin JSON Assertions
date: "2017-08-29 19:24:40 -0500"
---

I've just released a new project called [Kotlin Json Assert](https://github.com/gregwoodfill/kotlin-json-assert) on GitHub. It is a library for asserting JSON with Kotlin, that uses the style of the [Kluent](https://github.com/MarkusAmshove/Kluent) style assertions for JSON project. It is a thin wrapper over the excellent [JSONAssert](https://github.com/skyscreamer/JSONassert) library.

## Sample Usage
```kotlin
// strict checking is off by default
 """{"firstName": "Bob", "lastName":"Smith"}""" shouldEqualJson """{ "firstName": "Bob" }"""
"{}" shouldNotEqualJson """{"firstName":"Bob"}"""
```

```kotlin
// strict checking can be applied with `should strictly equal`
"""{"firstName": "Bob"}""" shouldStrictlyEqualJson """{ "firstName": "Bob" }"""
```
