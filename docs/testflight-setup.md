# Sending Arrowgami to TestFlight

You do this setup once. It all happens in a web browser, and an iPad is fine. After that, every build is one tap in GitHub.

## 1. Create the app in App Store Connect
1. Go to [appstoreconnect.apple.com](https://appstoreconnect.apple.com), then **Apps** → **+** → **New App**.
2. Fill it in:
   - **Platform:** iOS
   - **Name:** Arrowgami
   - **Primary language:** English (U.S.)
   - **Bundle ID:** `app.arrowgami.game`. If it isn't in the list, register it first: in [developer.apple.com → Identifiers](https://developer.apple.com/account/resources/identifiers/list), tap **+**, choose **App IDs**, then **App**, and enter the ID with the description "Arrowgami".
   - **SKU:** `arrowgami`
3. Tap **Create**.

## 2. Make an API key so GitHub can upload for you
1. In App Store Connect, go to **Users and Access** → **Integrations** → **App Store Connect API**. You may need to tap **Request Access** the first time.
2. Tap **+** (Generate API Key). Name it `GitHub Arrowgami` and set the access to **Admin**. Admin is needed so GitHub can create the signing certificates.
3. Write down the **Key ID** and the **Issuer ID** shown above the list.
4. Tap **Download API Key**. You get a file named like `AuthKey_ABC123.p8`. **You can only download it once.** Open it in a text editor or the Files app and copy all of its text, including the `-----BEGIN PRIVATE KEY-----` and `-----END PRIVATE KEY-----` lines.
5. Find your **Team ID** at [developer.apple.com → Membership details](https://developer.apple.com/account#MembershipDetailsCard). It's 10 characters, like `A1B2C3D4E5`.

## 3. Add the four secrets to GitHub
In the repository, go to **Settings** → **Secrets and variables** → **Actions** → **New repository secret**, and add each of these:

| Name | Value |
| --- | --- |
| `APP_STORE_CONNECT_KEY_ID` | the Key ID |
| `APP_STORE_CONNECT_ISSUER_ID` | the Issuer ID |
| `APP_STORE_CONNECT_KEY` | the full text of the .p8 file |
| `APPLE_TEAM_ID` | your Team ID |

Only GitHub's build machine can read these. Nobody can see them again after you save them, not even you.

## 4. Send a build
1. Go to the repository's **Actions** tab → **iOS build** → **Run workflow**. Leave "Upload to TestFlight" ticked and tap **Run workflow**.
2. The build is done when the run turns green. Apple then takes a few more minutes to process it before it shows up in App Store Connect → **TestFlight**.
3. Install the **TestFlight** app on your iPhone or iPad. Then add yourself under **Internal Testing** in App Store Connect, and the build appears in the TestFlight app.
