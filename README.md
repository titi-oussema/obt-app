# OBT - Only Better Traders (test app)

One codebase, three ways to use it:

| Where | How |
|---|---|
| Android app | GitHub builds an `.apk` automatically on every update (see below) |
| iPhone | Open the website in Safari → Share → **Add to Home Screen** |
| Computer | Open the website in any browser |

## Get the Android test app

1. Put this folder in a GitHub repository (branch `main`).
2. Open the repository → **Actions** tab. The job **Build Android test app** starts by itself (about 5–8 minutes).
3. When it is green, open **Releases** (right side of the repo page) → **OBT test build N** → tap `OBT-test-N.apk`.
4. On the phone: open the downloaded file → allow **Install unknown apps** if asked → **Install**.
5. Send the same `.apk` to testers (WhatsApp, Telegram, Drive). Each new update makes a new build number.

To rebuild by hand: **Actions** → **Build Android test app** → **Run workflow**.

## Put the website online (for iPhone testers)

1. Go to vercel.com → **Add New… → Project** → import this GitHub repository.
2. Framework preset: **Other**. Leave the build command empty. Click **Deploy**.
3. You get a link like `obt-app.vercel.app`. iPhone: open it in Safari → Share → **Add to Home Screen**.
   Android Chrome also shows **Install app**.

## Folder map

- `public/` – the app itself (`index.html`), app icons, offline support
- `android/` – the Android app project (Capacitor)
- `capacitor.config.json` – app name `OBT`, app id `com.obt.app`
- `.github/workflows/android.yml` – builds the `.apk`

## Updating the app

Edit `public/index.html`, push to `main`, and a new `.apk` appears in Releases.
For the website, also raise `VERSION` in `public/sw.js` so phones fetch the new version.

## Important

This is a test build. Accounts and posts are saved on each phone only, so testers
cannot see each other yet. The next step is connecting a real database (Supabase).
The test build is not signed for the Play Store; publishing uses a signed release build.
