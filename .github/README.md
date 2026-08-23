# Art Rotator — policy pages

Live at **https://profmcc.github.io/art-rotator/**

- [Privacy Policy](https://profmcc.github.io/art-rotator/privacy.html)
- [Support](https://profmcc.github.io/art-rotator/support.html)

These two URLs are what App Store Connect requires under **App Privacy →
Privacy Policy URL** and **App Information → Support URL**. They must keep
resolving for as long as the app is listed, so treat the paths as fixed.

## What Art Rotator is

An app that rotates open-access museum artwork onto your Lock Screen (iOS) or
desktop (macOS), cropped to your screen and captioned with the title, artist and
year. Sources are the Met, the Art Institute of Chicago, the Cleveland Museum of
Art, the National Gallery of Art, SMK, Japan Search and Wikimedia Commons.

It collects no personal data, has no accounts, no analytics and no tracking, and
never uploads anything. The privacy policy explains why that is a structural
property of the app rather than a promise.

## Why this repository has no source code

It is public purely to serve the two pages above. The app source is not
published; a `.gitignore` excludes everything except `docs/` so that stays
deliberate rather than accidental.

## Editing the pages

They are self-contained HTML — no build step, no scripts, no external requests,
light and dark aware. Edit, commit, push; GitHub Pages redeploys in about a
minute.

The privacy policy makes specific factual claims about what the app does and
does not do. If a future version adds analytics, an account, a crash-reporting
SDK, or any new network destination, **update the policy in the same release**,
not afterwards.
