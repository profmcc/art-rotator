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

## Already published

Live on GitHub Pages from `profmcc/art-rotator`, branch `main`, folder `/docs`:

| Page | URL |
|---|---|
| Landing | https://profmcc.github.io/art-rotator/ |
| Privacy Policy | https://profmcc.github.io/art-rotator/privacy.html |
| Support | https://profmcc.github.io/art-rotator/support.html |

Paste the last two into App Store Connect under **App Privacy → Privacy Policy
URL** and **App Information → Support URL**.

To update a page: edit it here, commit, push. Pages redeploys in about a
minute. The paths must keep resolving for as long as the app is listed, so
rename nothing.

**That repository is public and the app source is not in it.** A `.gitignore`
at the repo root excludes everything except `docs/` and `.github/`, so a stray
`git add .` cannot publish an unreleased codebase. Opening the source later
should be a deliberate act: delete that file, read `git status`, then push.

The pages are self-contained — no scripts, no fonts, no external requests,
light and dark aware, verified making zero third-party requests when served.
Any static host would work equally well if you later move to your own domain.

## Keep them true

The privacy policy makes a specific factual claim — that the app collects
nothing and contacts only the six named museum APIs. That is accurate for the
current build and is enforced by the code and its tests. If a future version
adds analytics, an account, a crash-reporting SDK, or any new network
destination, **update the policy in the same release**, not afterwards.
