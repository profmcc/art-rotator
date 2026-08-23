# Hosting the two App Store URLs

App Store Connect requires a **privacy policy URL** and a **support URL**, and
both must resolve to real, working pages on a stable address you control. A 404
or a generic landing page gets flagged during review.

## Contact address

Both pages publish **profmccarthy@protonmail.com** as `mailto:` links (two
occurrences each). The `{{SUPPORT_EMAIL}}` placeholder and the dashed
"unfilled" box that carried it are gone.

To change it:

```bash
cd docs
sed -i '' 's/profmccarthy@protonmail.com/you@yourdomain.com/g' privacy.html support.html
grep -c "you@yourdomain.com" privacy.html support.html   # expect 2 and 2
```

**Worth revisiting before launch.** This address goes on a public App Store
listing and will attract spam, and App Review may write to it — a dedicated
`support@yourdomain.com` on a domain you own is better than a personal inbox,
and it survives changing mail providers. Whatever you use, make sure it is
monitored: an unanswered support address is a common source of review friction.

## Publish free with GitHub Pages

```bash
cd ~/art-rotator-ios
git init -b main                    # if not already a repo
git add docs && git commit -m "Add privacy policy and support pages"
gh repo create art-rotator --public --source=. --push
```

Then in the repo: **Settings → Pages → Source: `main` / `docs`**. After a minute
the pages are live at:

- `https://<your-github-username>.github.io/art-rotator/privacy.html`
- `https://<your-github-username>.github.io/art-rotator/support.html`

Paste those into App Store Connect under **App Privacy → Privacy Policy URL**
and **App Information → Support URL**.

Any static host works equally well — Cloudflare Pages, Netlify, or your own
domain. The pages are self-contained: no scripts, no fonts, no external
requests, light and dark aware.

## Keep them true

The privacy policy makes a specific factual claim — that the app collects
nothing and contacts only the six named museum APIs. That is accurate for the
current build and is enforced by the code and its tests. If a future version
adds analytics, an account, a crash-reporting SDK, or any new network
destination, **update the policy in the same release**, not afterwards.
