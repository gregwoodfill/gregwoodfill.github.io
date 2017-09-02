---
layout: post
title: "JUnit Rules with Kotlin"
date: "2017-09-02 09:44:47 -0500"
---
While testing a service with WireMock, which uses a JUnit @Rule, we ran into an issue
where JUnit rules are supposed to be private final fields, Kotlin does not directly support
fields, and instead has properties that had field access.

The solution is to use Kotlin's @JvmField annotation as well as marking the field as final.

```kotlin
@Rule
@JvmField
final val wireMockRule = WireMockRule(8181)
```
