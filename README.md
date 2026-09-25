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

## Still to do before the stores
- Real rewarded ads and interstitials (Google AdMob). They replace the placeholder in `playAd()`.
- A "Remove ads" purchase and hint packs.
- The app icon, splash screen and store screenshots.
- Cloud builds, because there's no Mac: iOS builds to TestFlight on a macOS GitHub Actions runner, plus the Android release bundle.
- A privacy policy page (required because the app shows ads).
