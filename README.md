# TeleDrive Releases

This repository hosts public release metadata for TeleDrive Android APK updates distributed outside the Play Store.

## Public Release Endpoints

* **Manifest URL (JSON)**:  
  `https://raw.githubusercontent.com/sreejan-anand/teledrive-releases/main/android/latest.json`
* **Latest APK Download URL**:  
  `https://github.com/sreejan-anand/teledrive-releases/releases/latest/download/TeleDrive.apk`

---

## Important Rules

### 1. Do Not Commit APK Files Directly
> [!WARNING]
> Do not commit or push `.apk` files directly to this repository. The repository is only meant to store metadata files like JSON manifests.

### 2. Upload APKs as GitHub Release Assets
All compiled Android APK binaries must be uploaded manually as assets to the [GitHub Releases](https://github.com/sreejan-anand/teledrive-releases/releases) page. The APK asset name must be exactly:
```text
TeleDrive.apk
```

### 3. Version Code Management
For every new public APK release, you must increase the `versionCode` in `android/latest.json`. This is crucial for the application to detect that a newer update is available.

* `versionName` should match the Flutter app's version name.
* `versionCode` must match the Flutter app's build number.

#### Mapping Example:
* **Flutter version `1.0.0+1`** means:
  * `versionName` = `1.0.0`
  * `versionCode` = `1`

* **Flutter version `1.0.1+2`** means:
  * `versionName` = `1.0.1`
  * `versionCode` = `2`

---

For step-by-step instructions on how to publish a new release, please consult the [Manual Release Checklist](docs/manual-release-checklist.md).
