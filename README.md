# privacy

Privacy policy for Do It Up apps, served by GitHub Pages at
**<https://doitup-ca.github.io/privacy/>**

**➜ Picking this up in a new session?** The handoff is in the `hearth` repo and covers this one:
`gh api repos/bogez/hearth/contents/docs/handoff.md --jq .content | base64 -d`. There is no status
doc here on purpose — see [CLAUDE.md](CLAUDE.md).

That URL is what goes in the Google Play Console (Store listing → Privacy policy)
and it must stay publicly reachable and un-gated for as long as any app is listed.

## Scope

Developer-scoped, not per-app: one policy covering every Do It Up application, so
a second app does not need a second page. Currently covers **Hearth** (listed as
Hearth Launcher).

## Editing

`index.html` is the whole site — no build step, no dependencies, no framework.
Edit it, commit to `main`, and Pages redeploys.

Update the date whenever the content changes. ⚠️ **It appears twice** — in the
hero meta line under the title, and again in the footer. Both say
`3 SEPTEMBER 2026` today, and a stale footer is the easy half to miss:

```bash
grep -n "SEPTEMBER 2026" index.html
```

## What the styling assumes

Three rules `index.html` follows. Each looks like an arbitrary choice, is not,
and is the kind of thing a later edit undoes for tidiness. The reasoning, with
the measured numbers, is in the comment at the top of the stylesheet.

- **No webfont is fetched.** The font stacks name Inter and JetBrains Mono but
  request nothing from a CDN. A policy page that phoned a third party to render
  the sentence "these apps talk to no third party" would be its own
  counter-example. **The file now links out to nothing at all** — the last
  external URL was the `open-meteo.com` link in the Weather section, removed
  2026-09-06 with the feature it described. Keep it that way: if webfont
  fidelity ever matters more, self-host the `woff2` files here rather than
  linking out.
- **Two colours sit above the design system's values**, because the design's
  were under the WCAG AA 4.5:1 floor for small text. Lowest ratio on the page is
  now 5.47:1. `--primary` survives for the progress rule only, which is a
  graphic and owes just 3:1.
- **The tables are real `<table>` markup** styled to look like the design's
  panels. This is a legal document, so the row-to-column relationship has to
  survive a screen reader. Do not replace them with `div` grids.

## Keeping it true

The policy makes specific factual claims about the app, and if any of them stops
being true the policy must change **in the same release**.

⭐ **That list is not here.** It is a constraint on the app, not on this page, so
it lives where the app changes — `docs/security.md` §3 in the Hearth repo, which
is the authoritative copy. A list kept here would be read only by someone
editing the one HTML file, which is never the moment it matters.

The Play Console **Data safety** form must agree with this page. They are checked
against each other by Google, and a mismatch is a listing problem.
