---
sidebar_position: 2
title: Installation
---

# Installation

Add the YueMi Maven repository and the dependency to your plugin's `build.gradle.kts`:

```kotlin
repositories {
    maven { url = uri("https://repo.yuemi.my.id/repository/maven-releases/") }
}

dependencies {
    implementation("org.yuemi:mc-config-libs:1.0.0")
}
```

:::tip[Shade and Relocate]
Because the library is not bundled with the server, you must shade it into your plugin JAR and relocate the package to avoid class conflicts with other plugins on the server.

Configure the [Shadow Gradle plugin](https://gradleup.com/shadow/) in your `build.gradle.kts`:

```kotlin
tasks.named<com.github.jengelman.gradle.plugins.shadow.tasks.ShadowJar>("shadowJar") {
    relocate("org.yuemi.config", "${project.group}.libs.config")
}
```
:::

