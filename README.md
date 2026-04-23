> **NOTICE: Temporary Fork — Not Maintained**
> This is a temporary fork of [valhalla-openapi-models-kotlin](https://github.com/Rallista/valhalla-openapi-models-kotlin).
> It is published to GitHub Packages for internal use only and is **not actively maintained**.
> For production use, please use the upstream library from Maven Central.

# Valhalla Mobile OpenAPI Kotlin

Kotlin serializable [Valhalla](https://github.com/valhalla/valhalla) API and configuration models.

- **Valhalla Models** - Serializable models used for interacting with Valhalla's JSON APIs.
- **Valhalla Config Models** - Serializable models used for generating Valhalla's JSON config object.

## Usage

### Kotlin Gradle

Using a [`libs.versions.toml`](https://developer.android.com/build/migrate-to-catalogs) 

```toml
[versions]
valhallaModels = "0.0.8"
[libraries]
valhalla-models-config = { group = "io.github.rallista", name = "valhalla-models-config", version.ref = "valhallaModels" }
valhalla-models-api = { group = "io.github.rallista", name = "valhalla-models", version.ref = "valhallaModels" }
```

```kt
implementation(libs.valhalla.models.api)
implementation(libs.valhalla.models.config)
```

### Kotlin Gradle

```
implementation("io.github.rallista:valhalla-models-config:0.0.8")
implementation("io.github.rallista:valhalla-models:0.0.8")
```

### Gradle

```groovy
implementation 'io.github.rallista:valhalla-models-config:0.0.8'
implementation 'io.github.rallista:valhalla-models:0.0.8'
```

## GitHub Packages

### Triggering a Publish

Go to the **Actions** tab → select **"Publish to GitHub Packages"** → click **"Run workflow"**.

No inputs required. The published version is whatever is set in `settings.gradle.kts`.

### Consuming from GitHub Packages

GitHub Packages requires authentication even for public packages. Create a GitHub Personal Access Token (PAT) with the `read:packages` scope and store credentials in `~/.gradle/gradle.properties` (never commit this file):

```properties
gpr.user=YOUR_GITHUB_USERNAME
gpr.key=YOUR_GITHUB_PAT
```

Add the repository to your project's `settings.gradle.kts`:

```kotlin
dependencyResolutionManagement {
    repositories {
        maven {
            name = "GitHubPackages"
            url = uri("https://maven.pkg.github.com/OWNER/REPO")
            credentials {
                username = providers.gradleProperty("gpr.user").orNull ?: System.getenv("GITHUB_ACTOR")
                password = providers.gradleProperty("gpr.key").orNull ?: System.getenv("GITHUB_TOKEN")
            }
        }
    }
}
```

Replace `OWNER/REPO` with the actual repository path (e.g. `gabrielsamojlo/valhalla-openapi-models-kotlin`).

Then add dependencies as usual:

```kotlin
implementation("io.github.rallista:valhalla-models:0.1.1")
implementation("io.github.rallista:valhalla-models-config:0.1.1")
```

## What's Using It

- [valhalla-mobile](https://github.com/Rallista/valhalla-mobile) - A valhalla wrapper library built for Android & iOS.