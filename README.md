# Haunt: app project

This folder holds the game (in `www/index.html`) and a Capacitor config that wraps it as an iOS and Android app.

## Before you start: edit these 3 things
1. `capacitor.config.json`: change `appId` to something unique that you own, like `com.yourcompany.haunt`. It can't be changed easily after you publish.
2. `www/index.html`: the owner (ReliveGames) and contact email are already set. Search for `OWNER` if you want to change them.
3. Search `www/index.html` for `rewardedAd` and read the comment above it. It is a placeholder ad. See "Real ads" below.

## What you need
- Node.js (nodejs.org), LTS version.
- For iOS: a Mac with Xcode (free in the Mac App Store), plus an Apple Developer account (paid yearly).
- For Android: Android Studio (Windows, Mac or Linux), plus a Google Play Console account (one-time fee).
Check each company's site for current prices and requirements.

## Setup (once)
Open a terminal in this folder and run:

    npm install @capacitor/core @capacitor/cli @capacitor/ios @capacitor/android
    npm install -D @capacitor/assets
    npx cap add ios        # Mac only
    npx cap add android
    npx cap sync

## Run it on a phone
- iOS:     `npx cap open ios`, then in Xcode pick your iPhone and press Run. Set your Team under Signing & Capabilities.
- Android: `npx cap open android`, then in Android Studio pick a device or emulator and press Run.

Every time you change `www/index.html`, run `npx cap sync` again.

## Icon and splash screen
Put a 1024x1024 `icon-only.png` (and optionally `splash.png`, 2732x2732) in a folder named `assets`, then run:

    npx capacitor-assets generate

## Real ads
The ad in the game is only a placeholder countdown. For real rewarded ads, use an ad SDK plugin such as Google AdMob. In `www/index.html`, replace the body of `rewardedAd()` with the SDK call, and resolve `true` only when the SDK says the reward was earned. Follow your ad provider's setup guide for app IDs and test ads. Use test ads while developing, and never tap your own live ads.

## In-app purchases
For "remove ads" or skins, use a purchase plugin that works with Apple's and Google's billing, and add a Restore Purchases button. Digital items must use the store's own purchase system.

## Before you submit
- Add a privacy policy page and link it in the store listings and inside the app.
- Fill in Apple's App Privacy labels and Google Play's Data safety form honestly. Ads usually count as data collection.
- If you add accounts, you must also add in-app account deletion. Apple may also require Sign in with Apple if you offer other social logins.
- Don't target children unless you follow the kids' rules, which restrict ads and data.
- Test on real devices. Use TestFlight (iOS) and Internal testing (Android) before going public.
- Keep signing keys, keystores and passwords private and backed up. Turn on two-factor authentication on your developer accounts.

## No Mac?
You can't build iOS without macOS. Options: rent a cloud Mac, use a build service such as Codemagic, or borrow a Mac for the build and upload steps. Android works on Windows and Linux.

## Ownership
The game screen shows a copyright line and a Terms page. Have a lawyer review the terms before launch, and consider registering the name as a trademark.
