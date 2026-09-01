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

Update the date at the top whenever the content changes.

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
