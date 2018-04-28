---
layout: post
title: "Kotlin + Spring Boot's ConfigurationProperties"
date: "2018-04-27 13:45:47 -0500"
---
One minor annoyance i ran into with Spring Boot + Kotlin was that I couldn't find good documentation on getting
Intellij's autocompletion working with Kotlin classes annotated with @ConfigurationProperties.

ConfigurationProperties can be used to bind property values from application-[profile].properties or application.yml instead of
using @Value. The benefits are discussed in many places around the web.

For awhile I was just using Java for my ConfigurationProperties class, adding private fields and creating getters and setters.
That works, but getting them working in Kotlin is trivial if you know what to do and results in a lot less boiler plate.

The biggest issue thing is that you need to use kapt, the Kotlin Annotation Processor. You also need to tell kapt to
process resources using `org.springframework.boot:spring-boot-configuration-processor`

build.gradle
```groovy
plugins {
    apply plugin: 'kotlin-kapt'
}

dependencies{
    kapt "org.springframework.boot:spring-boot-configuration-processor"
	compileOnly "org.springframework.boot:spring-boot-configuration-processor"

}
compileJava.dependsOn(processResources)
```

Then you can just create a plain old Kotlin class that's annotated with @ConfigurationProperties
```kotlin
@ConfigurationProperties(prefix = "myapp")
class DemoConfigurationProperties {
    var url: URL? = null
}
```

In order for Intellij to autocomplete you just need to run gradle to the point of processing resources.
`./gradlew compileKotlin` does the trick.