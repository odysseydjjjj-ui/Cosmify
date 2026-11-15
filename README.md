
# Cosmify

Cosmify is a .NET MAUI starting implementation for Android and Windows using C#, XAML, MVVM-style view models and SQLite.

## Current implementation

- Dark purple interface and original SVG app icon.
- Local music file selection/import for MP3, FLAC, WAV, OGG, M4A, AAC and OPUS (subject to TagLib/MediaElement codec support on the target OS).
- Tag metadata extraction with TagLibSharp.
- SQLite persistence for tracks, playlists and playlist membership.
- Search across title, artist and album.
- Favorite flag storage and safe removal of library records (original media is not deleted).
- Playback surface wired through CommunityToolkit MediaElement.
- Honest integration catalogue for music/video providers and Discord; no fabricated content.

## Not yet implemented / not claimed

This is an initial functional foundation, not the complete feature set from the full specification. Background Android playback, lock-screen MediaSession controls, Windows global hotkeys, playlist management UI, cloud sync, video embeds/caching, Discord RPC, cover-art extraction/display, folder import and comprehensive tests still need platform-specific work. Provider APIs and credentials must be verified and supplied where required.

## Requirements

- .NET 10 SDK
- MAUI workloads for Android and Windows
- Android SDK / JDK for Android builds
- Windows 10/11 and Windows App SDK tooling for Windows builds

## Build

Run PowerShell from the repository root:

```powershell
./scripts/restore.ps1
./scripts/build-android.ps1
./scripts/build-windows.ps1
```

Android output is published under:
`src/Cosmify/bin/Release/net10.0-android/publish/`

Windows output is published under:
`src/Cosmify/bin/Release/net10.0-windows10.0.19041.0/win10-x64/publish/`

APK signing: create a keystore with `keytool`, keep it outside source control, then configure the Android signing properties for your release pipeline. Never commit signing keys.

## Notes

- SQLite data is stored in the app's private application data directory.
- Import uses the system file picker. Android folder-tree import and persistent URI permission support require an additional platform implementation.
- Removing a track removes only its database record and playlist references; it does not delete the original file.
- All integrations remain marked as not connected / requiring configuration until an actual adapter is implemented and verified.
