# Arrowgami

**Arrowgami: Arrow Escape Puzzle** for iPhone and Android. Tap an arrow to slide it off the board. If it bumps into anything, you lose a heart.

The whole game is one web page, `www/index.html`. [Capacitor](https://capacitorjs.com) wraps that page into the native `ios/` and `android/` apps.

## Working on it

```sh
npm install
npx cap sync        # copy www/ into the native projects after any game change
npx cap open android  # needs Android Studio
npx cap open ios      # needs a Mac with Xcode
```

## Ads
Google AdMob shows rewarded videos (an extra heart, or 2 hints) and, from level 10 on, a full-screen ad at most every 3 levels. **Google's test ads are on for now.** To switch to real ads:
1. Create the app in AdMob, once for iOS and once for Android.
2. Put the app IDs in `ios/App/App/Info.plist` (`GADApplicationIdentifier`) and `android/app/src/main/res/values/strings.xml` (`admob_app_id`).
3. Put the ad unit IDs in `AD_UNITS` in `www/index.html` and set `TEST_ADS = false`.

In a web browser the game shows a 3-second placeholder instead of an ad.

## Builds (no Mac needed)
- **Android:** every push builds a debug APK. You can download it from the workflow run's artifacts.
- **iOS:** to build, go to Actions → "iOS build" → Run workflow. That builds a signed release on GitHub's Mac and uploads it to TestFlight. It needs these repository secrets: `APP_STORE_CONNECT_KEY_ID`, `APP_STORE_CONNECT_ISSUER_ID`, `APP_STORE_CONNECT_KEY` (the text of the .p8 file) and `APPLE_TEAM_ID`.

## Still to do before the stores
- A "Remove ads" purchase and hint packs.
- The app icon, splash screen and store screenshots.
- A signed Android release bundle for Google Play.
- A privacy policy page (required because the app shows ads).
