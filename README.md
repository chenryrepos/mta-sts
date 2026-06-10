# mta-sts.lotjitsu.com

Static host (GitHub Pages) for **lotjitsu.com** email-security assets. Served over HTTPS at
`https://mta-sts.lotjitsu.com` via the `CNAME` file + a Squarespace `mta-sts` CNAME → `chenryrepos.github.io`.

## What it serves
- **`/.well-known/mta-sts.txt`** — the MTA-STS policy. Currently `mode: testing` (reports only, does not
  enforce). DNS side: `_mta-sts.lotjitsu.com` TXT = `v=STSv1; id=<datestamp>`.
- **`/lotjitsu-bimi.svg`** — BIMI logo (SVG Tiny P/S). **Placeholder** traced from the app icon; replace with
  the designer's real vector export before BIMI goes live. Not referenced by DNS yet (`default._bimi` unpublished).
- **`.nojekyll`** — required so GitHub Pages serves the `.well-known/` directory.

## TODO (≈2 weeks after 2026-06-09, once reports are clean)
1. MTA-STS: change `mode: testing` → `enforce` in `mta-sts.txt`, and **bump the `id`** in the `_mta-sts` DNS
   TXT record (signals senders to re-fetch).
2. DMARC: tighten `p=none` → `quarantine` → `reject`; SPF `~all` → `-all`.
3. BIMI (near launch): swap in the real vector logo, obtain a VMC (needs registered trademark) or CMC
   (needs 12mo public logo history), host the `.pem`, then publish `default._bimi`.
