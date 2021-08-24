# Build Gradle Infrastructure

We prefer to use Kotlin Programming Language in Build Gradle files.
- We define Android configuration (Application ID, MIN_SDK_VERSION etc.) with BuildAndroidConfig static class.
- We use a static class for Dependencies, we retrieve our versions from our BuildDependenciesVersions named class.
- We pay great attention to use kotlin to define all the values that could be variable.
- We use this [plugin](https://plugins.gradle.org/plugin/name.remal.check-dependency-updates) to check updates for dependencies inside the Build.gradle.

## Project Files

```text

├── ProjectFolder
  ├── app
    ├── build.gradle.kts
    ├── ...

  ├── buildSrc
    ├── src
      ├── main
        ├── kotlin
          ├── commons
            ├── android-library.gradle.kts
            ├── kotlin-library.gradle.kts
          ├── plugins
            ├── git-hooks.gradle.kts
            ├── ktlint.gradle.kts
            ├── ...
          ├── utils
            ├── BuildUtils.kt
          ├── BuildAndroidConfig.kt
          ├── BuildDependenciesVersions.kt
          ├── BuildModules.kt
          ├── BuildPlugins.kt
          ├── BuildType.kt
          ├── Dependencies.kt
    ├── build.gradle.kts
    ├── ...
  
  ├── data
    ├── build.gradle.kts
    ├── ...
  
  ├── domain
    ├── build.gradle.kts
    ├── ...
    
  ├── build.gradle.kts
  ├── settings.gradle.kts
  ├── ...

```
### android-library.gradle.kts
- We write our build logics, which we use repeatedly in our commons package as plugin and apply these plugins to our modules.
- We keep our applied plugins configurations in plugins packages files that we created.

```text

├── buildSrc
    ├── src
      ├── main
        ├── kotlin
          ├── commons
            ├── android-library.gradle.kts
       
```

