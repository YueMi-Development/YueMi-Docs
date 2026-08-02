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

:::tip[Shade it in]
Because the library is not bundled with the server, you must shade it into your plugin JAR using the [Shadow Gradle plugin](https://gradleup.com/shadow/).
:::
