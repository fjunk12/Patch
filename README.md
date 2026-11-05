# rif patches for Morphe

A Morphe port of [MojiRS/revanced-rif-patches](https://github.com/MojiRS/revanced-rif-patches) v1.7.2
(GPLv3) for **rif is fun 5.6.22**: the free app (`com.andrewshu.android.reddit`) and golden platinum
(`com.andrewshu.android.redditdonation`).

Patches: Disable ads (free only), Inline comment images, Fix comment video links, Fix imgur albums,
Fix YouTube videos, YouTube player controls, Fix share links. See [PATCHES.md](PATCHES.md).

## Get the .mpp

Every push runs `.github/workflows/build.yml`, which builds `patches-<version>.mpp` and attaches it
(also as `patches.mpp`) to the `v<version>-morphe` pre-release under **Releases**.
In Morphe Manager, add that file as a local patch source.

## Build locally

Requires JDK 21, the Android SDK, and a GitHub token with `read:packages` in `~/.gradle/gradle.properties`
(`gpr.user=<user>`, `gpr.key=<token>`). Then run `./gradlew :patches:buildAndroid`.

## What changed in the port

- Uses the `app.morphe.patches` Gradle plugin 2.1.0 and Morphe patcher 2.2.0 (from the Morphe patches template).
- `app.revanced.patcher.*` imports now point to `app.morphe.patcher.*`.
- `fingerprint { custom { … } }` is now `Fingerprint(custom = { … })`. `proxy(…).mutableClass` is now
  `mutableClassDefBy(…)`, and `classes` lookups use `classDefForEach` / `classDefBy`.
- The extension is `extensions/extension.mpe` instead of `.rve`. Compatibility is declared with Morphe `Compatibility` objects.
- The extension's Java code is unchanged.
