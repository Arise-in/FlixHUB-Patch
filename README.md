# FlixHub TV OTA Patch Channel (`Arise-in/FlixHUB-Patch`)

This folder is the template for the dedicated public GitHub repository [`https://github.com/Arise-in/FlixHUB-Patch`](https://github.com/Arise-in/FlixHUB-Patch) used by FlixHub TV for zero-config self-updates.

## Endpoints Used by the App
- **Primary manifest**: `https://raw.githubusercontent.com/Arise-in/FlixHUB-Patch/main/patch.json`
- **Fallback releases API**: `https://api.github.com/repos/Arise-in/FlixHUB-Patch/releases/latest`

## First-Time Repository Setup
```bash
git clone https://github.com/Arise-in/FlixHUB-Patch.git
cd FlixHUB-Patch
cp ../Android-tv-Flix/ota/FlixHUB-Patch-template/patch.json ./patch.json
cp ../Android-tv-Flix/ota/FlixHUB-Patch-template/README.md ./README.md
git add patch.json README.md
git commit -m "chore: initialize FlixHub TV OTA patch channel"
git push -u origin main
```

## Publishing a New OTA Release
Run `ota/publish-patch.ps1` from the main `Android-tv-Flix` workspace:

```powershell
.\ota\publish-patch.ps1 `
    -VersionCode 2 `
    -VersionName "1.0.1" `
    -ReleaseNotes @(
        "60fps D-Pad fluidity improvements",
        "Hardware ExoPlayer buffering tuning",
        "Improved OTA completion & auto-relaunch"
    ) `
    -PatchRepoPath "..\FlixHUB-Patch" `
    -Publish
```

The script:
1. Updates `versionCode`, `versionName`, and `PATCH_VERSION` in `app/build.gradle.kts`.
2. Builds `.\gradlew.bat assembleRelease`.
3. Computes the SHA-256 digest of `app/build/outputs/apk/release/app-release.apk`.
4. Updates `ota/patch.json` (and `<PatchRepoPath>\patch.json` if provided).
5. Commits, tags `v<VersionName>`, and with `-Publish` pushes `main` + tag and uploads `app-release.apk` via GitHub CLI (`gh release create`).

## `patch.json` Schema
| Field | Type | Description |
|---|---|---|
| `versionCode` | `int` | Monotonic Android `versionCode` checked against installed app |
| `versionName` | `string` | Semantic version (`"1.0.1"`) |
| `patchTag` | `string` | GitHub Release tag (`"v1.0.1"`) |
| `title` | `string` | Display title inside the OTA glass modal |
| `releaseNotes` | `string[]` | Bullet points shown in the modal (up to 6 rendered) |
| `apkUrl` | `string` | Direct download URL to `app-release.apk` |
| `sha256` | `string` | Optional lowercase SHA-256 checksum verified before installer launch |
| `isMandatory` | `bool` | Hides skip/later dismiss actions when `true` |
| `minSupportedVersionCode` | `int` | Minimum app `versionCode` eligible for direct upgrade |
| `publishedAt` | `string` | ISO-8601 UTC timestamp |
