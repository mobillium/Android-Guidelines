# Build Gradle Infrastructure
We prefer to use Kotlin Programming Language in Build Gradle files.
- We define Android configuration (Application ID, MIN_SDK_VERSION etc.) with BuildAndroidConfig static class.
- We use a static class for Dependencies, we retrieve our versions from our BuildDependenciesVersions named class.
- We pay great attention to use kotlin to define all the values that could be variable.
