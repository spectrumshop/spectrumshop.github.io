# spectrumshop.github.io

Public site for Spectrum. Exists primarily to satisfy TikTok's developer app
requirements: an app created after 9 September 2024 must have a verified
Terms of Service URL, Privacy Policy URL and website URL before it can be
submitted for review.

Served at **https://spectrumshop.github.io/** — plain static HTML, no build step.
Edit a file, commit, push; GitHub Pages redeploys in about a minute.

## Dropping in TikTok's verification file

TikTok gives you a file named something like `tiktokXXXXXXXXXXXX.txt`.

Put it in **the root of this repository** — alongside `index.html`, not in a
subfolder — then commit and push:

```bash
cd ~/Documents/spectrumshop-site
cp ~/Downloads/tiktokXXXXXXXXXXXX.txt .
git add tiktokXXXXXXXXXXXX.txt
git commit -m "Add TikTok domain verification file"
git push
```

It will be live at `https://spectrumshop.github.io/tiktokXXXXXXXXXXXX.txt`.
Confirm it resolves before clicking Verify in the TikTok dashboard:

```bash
curl -I https://spectrumshop.github.io/tiktokXXXXXXXXXXXX.txt   # expect 200
```

Use the **URL prefix** option with `https://spectrumshop.github.io/`.
DNS TXT verification is not possible here, since the `github.io` domain
belongs to GitHub rather than to us.

## Placeholders to fill before submitting for review

Every placeholder is marked `[ADD ...]` in the HTML and renders with a yellow
highlight, so anything unfilled is obvious on the page. Find them with:

```bash
grep -rn "\[ADD" .
```

- **Contact email** — appears on all four pages. A real monitored address;
  TikTok reviewers and customers both use it.
- **Name / trading name** — the sole trader name behind Spectrum.
- **Business address** — required for UK distance-selling compliance.

## A caveat worth keeping in mind

These documents follow UK GDPR, the Consumer Contracts Regulations 2013 and
the Consumer Rights Act 2015, but they were not written by a solicitor. They
are a reasonable starting position for a small UK sole trader, not a
substitute for legal advice once real money is moving.

Two things in particular will need revisiting when the store goes live:

- The Privacy Policy names categories of recipient (payment provider,
  fulfilment partner) rather than specific companies. Name them once the
  actual providers are chosen.
- Delivery timescales in the Terms should be checked against what the
  supplier actually commits to, rather than the other way round.

## Moving to a custom domain later

Add a `CNAME` file containing the domain, point the registrar's DNS at
GitHub Pages, and enable the domain in repo Settings → Pages. Page content is
unchanged. At that point domain-level DNS TXT verification with TikTok also
becomes available.
