# Releasing Brick Burst on Google Play

Everything in this folder is ready to upload. The steps below need your own Play Console account; nobody else can do them for you.

## Files

| What | File |
|---|---|
| App bundle to upload | `android/app/build/outputs/bundle/release/app-release.aab` |
| App icon (512×512) | `store/play-icon-512.png` |
| Feature graphic (1024×500) | `store/feature-graphic.png` |
| Phone screenshots (1080×1920) | `store/phone-1-levels.png` … `phone-4-cleared.png` |
| Privacy policy URL | https://divakar-docmx.github.io/brick-burst/privacy.html |

**Package name:** `io.github.divakardocmx.brickburst`. This can never change after your first upload.

## ⚠️ Back up the upload key

`~/brick-burst-signing/` holds `upload.keystore` and `keystore.properties` (which contains its password). Copy that folder somewhere safe, such as a password manager or an encrypted drive. Every future update has to be signed with this key. If you lose it, Google can reset it, but that takes days. Never commit it to Git.

## Steps

1. **Create a developer account** at https://play.google.com/console (one-time US$25 fee plus identity verification).
2. **Create app:** name *Brick Burst*, default language English, *Game*, *Free*.
3. **Set up your app** (the checklist on the dashboard):
   - **Privacy policy:** paste the URL above.
   - **App access:** *All functionality is available without special access.*
   - **Ads:** *No, my app does not contain ads.*
   - **Content rating:** fill in the questionnaire (category *Game*). Answer *No* to violence, sexual content, gambling, user interaction and sharing location. This normally comes out as *Everyone / PEGI 3*.
   - **Target audience:** choose **13+** (or 13–15, 16–17 and 18+). Choosing under 13 brings in Google's Families policy requirements.
   - **Data safety:** *No* to "Does your app collect or share any of the required user data types?". The app has no internet permission and keeps progress on the device.
   - **Government apps / financial features / health:** *No.*
4. **Store listing:** paste the text below and upload the icon, feature graphic and screenshots.
5. **Upload the bundle:** Testing → *Closed testing* → create a track → upload `app-release.aab`. Choose **Play App Signing** when asked (recommended).
6. **New personal accounts must run a closed test first:** at least **12 testers** opted in for **14 days in a row** before you can apply for production. Add their Gmail addresses as a tester list and share the opt-in link with them.
7. After 14 days, go to **Production** → *Create new release* → promote the same bundle → *Send for review*. Review usually takes a few days.

## Store listing text

**App name** (30 max)
> Brick Burst

**Short description** (80 max)
> Find the gap, burst every brick, and catch +3 to split your ball into three!

**Full description**
> Brick Burst is a calm-but-tense brick-breaker. A wall of thousands of tiny bricks sits behind a stone wall with a single small gap. Bounce your ball through the gap and watch it carve tunnels through the bricks, one burst at a time.
>
> Hit a yellow brick and a +3 falls. Catch it with your plank and the ball that broke it splits into three right where it is. Keep catching them and the screen fills with hundreds of balls.
>
> • 10 hand-made levels: Classic, Twin Gates, The Shelf, Three Rooms, Funnel, Cross, Zigzag, Pillars, Fortress and Needle
> • Pick any level at any time. Your cleared levels are remembered
> • Choose your ball speed with 10 speed levels, from relaxing to frantic
> • Steer the ball by moving the plank as it hits
> • Full screen, works completely offline, no ads, no tracking
>
> Patience, thrill and suspense: can you clear all ten?

**Category:** Game → Arcade
**Tags:** Arcade, Casual, Brick breaker

## Releasing an update later

1. Change the game files.
2. In `android/app/build.gradle`, raise `versionCode` by 1 and update `versionName` (for example 1.0.1).
3. Run `npm run aab:release` in the project folder. You need Android Studio's Java on your PATH: `export JAVA_HOME="/Applications/Android Studio.app/Contents/jbr/Contents/Home"`.
4. Upload the new `app-release.aab` in Play Console.
