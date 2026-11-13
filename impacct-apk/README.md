# IMPACCT Market Preview: Android app

A WebView wrapper (Capacitor) around the public preview dashboard in `www/index.html`. Everything is bundled, so it works offline except the Manrope and Inter web fonts, which fall back to system fonts when offline.

## Build the APK on your computer (Android Studio or the command line)
1. Install Node 18+, JDK 17 and the Android SDK (Android Studio installs the last two).
2. `npm install`
3. `npm run apk`
4. The file is at `android/app/build/outputs/apk/debug/app-debug.apk`. Copy it to a phone and open it (allow "install unknown apps").

## Build it without installing anything
Put this folder in a GitHub repository and run the "Build APK" workflow (Actions tab). Download `impacct-preview-apk` from the run.

## Updating the content
Rebuild the preview (`npx vite build --mode preview`), copy `dist-preview/index.html` over `www/index.html`, then `npm run apk`.

## Before releasing on Google Play
The debug APK is for testing. A Play Store release needs a signing key and an App Bundle (`./gradlew bundleRelease`). The app id is `info.impacct.preview`; change it in `capacitor.config.json` before the first release, as it cannot change later.
