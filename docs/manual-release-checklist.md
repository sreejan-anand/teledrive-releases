# Manual Release Checklist for TeleDrive Android

Follow this step-by-step checklist to prepare and publish a new sideloaded update for the TeleDrive Android application.

## Step 1: Update Application Version
In the main Flutter project repository, locate the `pubspec.yaml` file and increase the version name and build number.
```yaml
version: 1.0.1+2
```
* **Version Name (`1.0.1`)**: Used as `versionName` in the release manifest.
* **Build Number (`2`)**: Used as `versionCode` in the release manifest. Must always be incremented.

## Step 2: Build the Release APK
Run the following build command in the root of the Flutter project to compile a release build:
```bash
flutter build apk --release
```

## Step 3: Rename the Built APK Binary
After the build completes, navigate to the output folder (typically `build/app/outputs/flutter-apk/`) and rename the release APK file:
* **Original Name**: `app-release.apk`
* **New Name**: `TeleDrive.apk`

> [!IMPORTANT]
> The filename must be exactly `TeleDrive.apk`.

## Step 4: Create a New GitHub Release
Navigate to the [teledrive-releases repository on GitHub](https://github.com/sreejan-anand/teledrive-releases) and create a manual release:
1. Click **Releases** -> **Draft a new release**.
2. **Tag**: Create a tag representing the version, e.g., `v1.0.1`.
3. **Title**: Set a descriptive title, e.g., `TeleDrive 1.0.1`.
4. **Description**: Detail the changes in this version.

## Step 5: Upload the APK Asset
Attach the renamed `TeleDrive.apk` file to the GitHub Release as an asset, then publish the release.

## Step 6: Update the JSON Release Manifest
In this `teledrive-releases` repository, edit `android/latest.json` to match the newly published release.

### Example Manifest Configuration:
```json
{
  "android": {
    "versionName": "1.0.1",
    "versionCode": 2,
    "apkUrl": "https://github.com/sreejan-anand/teledrive-releases/releases/latest/download/TeleDrive.apk",
    "releaseNotes": [
      "Fixed upload lag.",
      "Improved app stability."
    ],
    "publishedAt": "2026-05-26T00:00:00Z",
    "sha256": "",
    "minimumSupportedVersionCode": 1,
    "mandatory": false
  }
}
```

## Step 7: Commit and Push Manifest Changes
Commit and push the update to `android/latest.json` to the remote branch:
```bash
git add android/latest.json
git commit -m "Update android release manifest to v1.0.1"
git push origin main
```

## Step 8: Verify the Release Links
Open your browser and verify that both of the following URLs are fully accessible:
1. **JSON Release Manifest**:  
   `https://raw.githubusercontent.com/sreejan-anand/teledrive-releases/main/android/latest.json`
2. **Latest APK Download (Redirects to latest release asset)**:  
   `https://github.com/sreejan-anand/teledrive-releases/releases/latest/download/TeleDrive.apk`
