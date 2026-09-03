# privacy

Privacy policy for Do It Up apps, served by GitHub Pages at
**<https://doitup-ca.github.io/privacy/>**

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

Two things in `index.html` look like arbitrary choices and are not. Both were
deliberate, and changing them back would break a claim this page makes:

- **No webfont is fetched.** The design asks for Inter and JetBrains Mono, and
  the font stacks name them, but they are used only if the reader already has
  them — nothing is requested from a font CDN. The page's whole claim is that
  the apps talk to no third party; a policy page that phoned a CDN to render
  that sentence would be its own counter-example. The only external URL in the
  file is the `open-meteo.com` link in the Weather section, and it is a link,
  not a request. **Keep it that way**: if fidelity matters more, self-host the
  `woff2` files in this repo rather than linking out.
- **Two colours sit above the design system's values.** Its `ink-tertiary`
  (#62666d) measured 3.1–3.6:1 behind the mono micro-labels and its accent
  measured 3.8–4.4:1 as text — both under the WCAG AA 4.5:1 floor for small
  text, on a page Google reads. The labels use `--ink-subtle` and accent text
  uses `--primary-strong`; the lowest ratio on the page is 5.47:1. `--primary`
  survives for the progress rule only, which is a graphic and owes just 3:1.
  The reasoning is repeated in a comment at the top of the stylesheet.

The tables are real `<table>` markup styled to look like the design's panels.
This is a legal document, so the row-to-column relationship has to survive a
screen reader — do not replace them with `div` grids.

## Keeping it true

The policy makes specific factual claims about the app. If any of these stop
being true, the policy must change **in the same release**:

- no analytics, crash reporting, or advertising SDKs
- no developer-operated server, and no account system
- credentials in Keystore-backed encrypted storage
- `allowBackup=false`
- no location permission requested
- outbound network limited to: the user's Home Assistant, the user's IPTV
  provider (and logo CDNs its playlist references), Open-Meteo for weather, and
  the platform speech recogniser for voice search
- unencrypted (HTTP) traffic is refused except to local addresses and to **one**
  IPTV provider host the user has explicitly approved, after being shown that
  their provider password travels in the clear. HTTPS is always tried first.
  See hearth#134 — if the consent screen is ever removed, weakened, or made to
  cover more than one host, the "Providers without encryption" section is wrong

The Play Console **Data safety** form must agree with this page. They are checked
against each other by Google, and a mismatch is a listing problem.
