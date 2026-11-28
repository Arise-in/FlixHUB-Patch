<div align="center">

<img src="assets/flixhub_logo.png" alt="FlixHUB Logo" width="140" />

# FlixHUB — TV & Mobile

**Cinema-grade streaming for Android TV, Google TV, and Android Mobile.**

[![TV Release](https://img.shields.io/badge/FlixHUB%20TV-v1.4.0%20Stable-0A84FF?style=for-the-badge)](https://github.com/Arise-in/FlixHUB-Patch/releases/tag/v1.4.0)
[![Mobile Release](https://img.shields.io/badge/FlixHUB%20Mobile-v1.0.0%20Stable-30D158?style=for-the-badge)](https://github.com/Arise-in/FlixHUB-Patch/releases/tag/mobile-v1.0.0)
[![Platforms](https://img.shields.io/badge/Platforms-Android%20TV%20%7C%20Google%20TV%20%7C%20Mobile-5E5CE6?style=for-the-badge)](https://github.com/Arise-in/FlixHUB-Patch/releases)
[![Downloads](https://img.shields.io/github/downloads/Arise-in/FlixHUB-Patch/total?style=for-the-badge&color=FF9F0A)](https://github.com/Arise-in/FlixHUB-Patch/releases)

[Download Releases](https://github.com/Arise-in/FlixHUB-Patch/releases) • [Platform Comparison](#-platform-comparison--specs) • [TV Previews](#-android-tv-previews) • [Mobile Previews](#-android-mobile-previews) • [Changelogs](#-changelogs)

</div>

---

## Download & Install

<!-- RELEASE_START -->
- **Latest TV Release:** [`v1.4.0`](https://github.com/Arise-in/FlixHUB-Patch/releases/tag/v1.4.0) • [Download `app-release.apk`](https://github.com/Arise-in/FlixHUB-Patch/releases/download/v1.4.0/app-release.apk)
- **Latest Mobile Release:** [`mobile-v1.0.0`](https://github.com/Arise-in/FlixHUB-Patch/releases/tag/mobile-v1.0.0) • [Download `flixhub-mobile-release.apk`](https://github.com/Arise-in/FlixHUB-Patch/releases/download/mobile-v1.0.0/flixhub-mobile-release.apk)
- **Total Downloads:** **10**
<!-- RELEASE_END -->

| Edition | Tag | Version (Build) | Target Devices | APK Size | SHA-256 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **FlixHUB TV** | [`v1.4.0`](https://github.com/Arise-in/FlixHUB-Patch/releases/tag/v1.4.0) | `1.4.0` (`versionCode 8`) | Android TV / Google TV (`minSdk 24`, `targetSdk 34`) | `12.29 MB` | `5eadeff75e767fd08902a4633097cf507207ab5e97331036e3f49cd709a64a0f` |
| **FlixHUB Mobile** | [`mobile-v1.0.0`](https://github.com/Arise-in/FlixHUB-Patch/releases/tag/mobile-v1.0.0) | `1.0.0` (`versionCode 5`) | Android Phones & Tablets (`minSdk 24`, `targetSdk 34`, 1GB+ RAM tuned) | `11.96 MB` | `4046e58e81e82b651226593ab833c23c935e53cb23e4931225306131dea581e6` |

1. Download the matching APK (**`app-release.apk`** for Android TV / Google TV, or **`flixhub-mobile-release.apk`** for Android Phones).
2. Install on your device (`Settings → Security → Install Unknown Apps`).
3. On Android TV, future updates can also be pulled in-app via **Settings → About → Check for Updates** (Ed25519 signature + SHA-256 verified).

---

## Android TV Previews

| Home & Translucent Sidebar | Title Detail & Extras |
| :---: | :---: |
| ![TV Home](assets/home.png) | ![TV Detail](assets/detail.png) |

| D-Pad Search & Provider Filters | Frosted Glass Player HUD |
| :---: | :---: |
| ![TV Search](assets/search.png) | ![TV Player HUD](assets/player.png) |

---

## Android Mobile Previews

<div align="center">
<table>
  <tr>
    <th align="center">Home &amp; Hero Billboard</th>
    <th align="center">Scrolled Blur &amp; Floating Bar</th>
    <th align="center">Detail &amp; Sticky Header Blur</th>
    <th align="center">Search &amp; Discovery</th>
    <th align="center">Frosted Profile &amp; Library</th>
  </tr>
  <tr>
    <td align="center"><img src="assets/mobile_home.png" alt="Mobile Home" width="180" /></td>
    <td align="center"><img src="assets/mobile_home_scrolled.png" alt="Mobile Scrolled Glass" width="180" /></td>
    <td align="center"><img src="assets/mobile_detail.png" alt="Mobile Detail Sticky Blur" width="180" /></td>
    <td align="center"><img src="assets/mobile_search.png" alt="Mobile Search" width="180" /></td>
    <td align="center"><img src="assets/mobile_profile.png" alt="Mobile Profile Glass" width="180" /></td>
  </tr>
</table>
</div>

---

## Platform Comparison & Specs

| Capability / Architecture | FlixHUB TV (`v1.4.0` Stable) | FlixHUB Mobile (`v1.0.0` Stable) |
| :--- | :--- | :--- |
| **UI Stack** | Kotlin + Jetpack Compose for TV (`androidx.tv`) | Kotlin + Jetpack Compose (`material3`) |
| **Navigation & Input** | 60fps D-Pad pivot scrolling (`BringIntoViewSpec`), wall locks, spring focus scaling (`AppleTvFocusable`), auto-hiding translucent sidebar + Top/Channel hubs | Floating frosted-glass bottom pill bar (`AppleFloatingGlassBottomBar`) with slide-to-switch haptic physics, top glass header, and zero-allocation `ModifierNodeElement` touch bounce |
| **Glass & Ambient Blur** | Real-time Haze `Performance` glass + pre-blurred `FastStackBlurTransformation` ambient backdrops | Real-time Haze `Performance` glass (capped at `12.dp`) + pre-blurred `FastMobileStackBlurTransformation` ambient canvases, automatic low-RAM scrim fallback |
| **1GB RAM & Scroll Tuning** | Leanback focus cache, deferred `800ms+` native trailer extraction (`WebView` disabled), Coil hardware bitmaps | `MobileCardImage` leaf isolation (no scroll-time `ImageRequest` rebuilds), subscriber-counted `BreathingClockRegistry`, bound-cancelled `animateDecay` fling physics, `128MB` / `16MB` low-RAM ExoPlayer cache, ART `baseline.prof` AOT |
| **Media & Streaming Engine** | Media3 ExoPlayer with dual audio tracks, playback speeds, SDH captions, skip-intro, multi-source streams, trailers | Media3 ExoPlayer landscape player (`1.0x–2.0x`, subtitles, audio tracks, InSight, Up Next, Next Episode) + Screenscape/VidNest/YouTube resolution |
| **Offline Library & Storage** | Watchlist, Watch History, external USB drive support, resumable 4K downloads | Persistent Watchlist, Offline Downloads, and Continue Watching / History tabs (`Library`) |
| **Security & Pairing** | Native C++ vault (`libflixcore.so` + AES-256-GCM `core.pak`), QR/Firebase pairing, Ed25519-signed OTA (`manifest.json.sig`) | Native C++ vault (`libflixcore.so` + AES-256-GCM `core.pak`), Firebase Auth & profile switching, V2 signed release with ART AOT profile |

---

## Key Features Across Both Editions

### FlixHUB TV (`v1.4.0` Stable)
- **tvOS-Inspired Cinema Interface:** Pure OLED black (`#000000`) canvas with Haze translucent side drawer, Hero Billboard auto-carousel, Top 10 ranking rows, Watchlist, FlixHUB+, Movies, TV Shows, Anime, Sports, and Provider Hubs.
- **Butter-Smooth 60fps D-Pad Navigation:** Custom focus restoration, horizontal pivot glide, wall locks (`tvWallLock`), and debounced UI navigation audio.
- **External USB & Offline Downloads:** Self-contained offline media storage with 4K multi-audio downloads, pause/resume/cancel controls, and frosted glass Episode/Info dialogs.
- **Signed In-App OTA Updates:** Cryptographically verified via Ed25519 (`manifest.json.sig`) and APK SHA-256 validation before installation.

### FlixHUB Mobile (`v1.0.0` Stable)
- **Floating Liquid-Glass Navigation:** Draggable bottom frosted-glass pill bar (`Home`, `Movies`, `Series`, `Anime`, `Library`, plus glowing `Search` orb) and sticky blurred top headers.
- **Engineered for Smooth Scrolling on 1GB+ RAM:** Eliminates Chromium `WebView` inflation during browsing, offloads ambient blur to pre-blurred `StackBlur` bitmaps, isolates Coil state inside leaf composables, and stops skeleton frame clocks when unmounted.
- **Full Detail & Companion Player:** Parallax hero + trailer autoplay preview, TMDB logos and `4K` / `Dolby Vision` / `Dolby Atmos` / `SDH` badges, Cast & Crew carousels, More Like This recommendations, and full-screen landscape Media3 playback.
- **Unified Account & Profiles:** Seamless Firebase account sign-in, profile switching, Watchlist / History sync, Auto-Play Next Episode, and Auto-Skip Intros toggles.

---

## Changelogs

<!-- CHANGELOG_START -->
### [`v1.4.0`](https://github.com/Arise-in/FlixHUB-Patch/releases/tag/v1.4.0) — FlixHUB TV v1.4.0 Stable (2026-11-28) • [Download `app-release.apk`](https://github.com/Arise-in/FlixHUB-Patch/releases/download/v1.4.0/app-release.apk)

Stable Android TV & Google TV release (`versionCode 8`).

### [`mobile-v1.0.0`](https://github.com/Arise-in/FlixHUB-Patch/releases/tag/mobile-v1.0.0) — FlixHUB Mobile v1.0.0 Stable (2026-11-28) • [Download `flixhub-mobile-release.apk`](https://github.com/Arise-in/FlixHUB-Patch/releases/download/mobile-v1.0.0/flixhub-mobile-release.apk)

Initial stable Mobile release (`versionCode 5`), tuned for 1GB+ RAM devices with butter-smooth Compose scrolling and preserved frosted-glass blur.

[Full Changelog](CHANGELOG.md)
<!-- CHANGELOG_END -->

---

## Star History

<a href="https://www.star-history.com/#Arise-in/FlixHUB-Patch&Date">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=Arise-in/FlixHUB-Patch&type=Date&theme=dark" />
    <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=Arise-in/FlixHUB-Patch&type=Date" />
    <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=Arise-in/FlixHUB-Patch&type=Date" />
  </picture>
</a>

---

<div align="center">
  <sub>An <strong>Aniflix</strong> Product • Built for Android TV, Google TV &amp; Android Mobile</sub>
</div>
