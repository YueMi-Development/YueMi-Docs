# YueMi Maven Repository

To use any of YueMi Development's public APIs (such as `BingoGacha-api`), you need to register the YueMi Maven Repository in your project build configuration.

## 📦 Repository URL

The public Maven repository is hosted at:
```
https://repo.yuemi.my.id/repository/maven-public/
```

---

## 🛠️ Build Configuration Examples

### Gradle (Kotlin DSL)
Add the repository to your `repositories` block:

```kotlin
repositories {
    mavenCentral()
    maven("https://repo.yuemi.my.id/repository/maven-public/")
}
```

### Gradle (Groovy DSL)
Add the repository to your `repositories` block:

```groovy
repositories {
    mavenCentral()
    maven {
        url "https://repo.yuemi.my.id/repository/maven-public/"
    }
}
```

### Maven (pom.xml)
Add the repository to your `<repositories>` tag:

```xml
<repositories>
    <repository>
        <id>yuemi-public</id>
        <url>https://repo.yuemi.my.id/repository/maven-public/</url>
    </repository>
</repositories>
```
