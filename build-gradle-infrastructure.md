# Build Gradle Infrastructure
We prefer to use Kotlin Programming Language in Build Gradle files.
- We define Android configuration (Application ID, MIN_SDK_VERSION etc.) with BuildAndroidConfig static class.
- We use a static class for Dependencies, we retrieve our versions from our BuildDependenciesVersions named class.
- We pay great attention to use kotlin to define all the values that could be variable.
- We write our build logics, which we use repeatedly in our commons package as plugin and apply these plugins to our modules.
- We keep our applied pluginses configurations in plugins packages files that we created.
- We primarily define variants that will we variable according to Build Variant at build gradle files. If we were to reach these variants at runtime we will use BuildConfig filed, if we were to reach at build time, we use resValues function.
- We Use this [plugin](https://plugins.gradle.org/plugin/name.remal.check-dependency-updates) to check updates for dependencies inside the Build.gradle.
