# Turning on real ads (Google AdMob)

The app shows Google's **test** ads until this is done.

1. Sign in at [admob.google.com](https://admob.google.com) with the Google account you want paid through. Add your payment and tax details for Asylum MKE LLC under **Payments**.
2. **Apps** → **Add app** → **iOS** → "No, it isn't listed yet" (you can link it to the store later) → name it **Arrowgami**. Leave user metrics on.
3. Inside that app, create **2 ad units**:
   - **Rewarded**, named `Rewarded - heart or hints`. Keep the default reward settings, because the game decides the reward itself.
   - **Interstitial**, named `Between levels`.
4. Do steps 2 and 3 again for **Android**.
5. Under **Privacy & messaging**, create a **GDPR** message and an **IDFA explainer** message (iOS), then publish both. They create the consent pop-ups the app already knows how to show.
6. Send Claude these 6 IDs. They're not secret.
   - iOS **App ID** (looks like `ca-app-pub-1234567890123456~1234567890`)
   - iOS **Rewarded** and **Interstitial** ad unit IDs (look like `ca-app-pub-…/…`)
   - Android **App ID**
   - Android **Rewarded** and **Interstitial** ad unit IDs

Once the apps are live in the stores, link each AdMob app to its store listing (**App settings** → **Add app store**). AdMob also asks you to host an `app-ads.txt` file on your developer website. It shows you the exact line to add.
