# privacy

⛔ **The handoff lives in the `hearth` repo, and it covers this one.** Read it before anything
else, every session. No clone needed:

```bash
gh api repos/bogez/hearth/contents/docs/handoff.md --jq .content | base64 -d
```

It is rewritten each session and is the working set for all three repos — the app
(`bogez/hearth`, moving to `doitup-ca/hearth`; the command follows the redirect), this policy,
and the site at `doitup-ca/hearthlauncher-web`. ⛔ **Do not start a status doc here.** A copy is
a doc that drifts.

## What this repo is

One public page — `index.html`, no build step — served by GitHub Pages at
<https://doitup-ca.github.io/privacy/>. See [README.md](README.md) for the editing rules, the
duplicated date, and the three styling choices that look arbitrary and are not.

## Three things to hold on to

⛔ **This URL goes in the Play Console and must stay publicly reachable and un-gated** for as
long as any app is listed. Nothing here may end up behind an access check.

⛔ **The claims this page makes about the app are constrained by `docs/security.md` §3 in the
`hearth` repo**, which is the authoritative list and says they change in the same release the
app does. The list is deliberately not duplicated here — it is a constraint on the app, and it
would be read here only by someone editing one HTML file, which is never the moment it matters.

⚠️ **The Play Console Data safety form must agree with this page.** Google checks them against
each other, and a mismatch is a listing problem rather than a documentation one.

⚠️ **When a claim is about behaviour, check the app's code, not a doc.** On 2026-09-04 the
marketing doc and the product site both described a security policy the app had replaced thirteen
days earlier; they agreed with each other and both were wrong.
