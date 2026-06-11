# The Hidden Cost of the FOG — VCM Financing Diagnostic

An interactive lead-magnet for Vanguard Captive Management. A prospect describes
their business in five inputs, and the tool draws the **FOG** — the Financing
Opportunity Gap — between the financing program they run today and a fully built
captive. One self-contained HTML file. No build step, no dependencies, nothing
leaves the browser.

**Live:** `https://<your-username>.github.io/<repo-name>/` *(fill in after step 3 below)*

---

## What's in here

| File | Purpose |
|------|---------|
| `index.html` | The entire tool — markup, styles, and engine in one file. |
| `.nojekyll` | Tells GitHub Pages to serve the file as-is. |
| `README.md` | This file. |

That's the whole site. The tool runs entirely client-side.

---

## Deploy to GitHub Pages (no command line)

1. Create a new repository on GitHub (e.g. `fog-diagnostic`). Keep it **Private**
   if you don't want the source public — Pages still serves it to anyone with the link.
2. Click **Add file → Upload files**, drag in `index.html` and `.nojekyll`, and commit.
3. Go to **Settings → Pages**. Under *Build and deployment*, set **Source = Deploy
   from a branch**, **Branch = main**, **Folder = / (root)**, and **Save**.
4. Wait ~1 minute. Pages prints your live URL at the top of that same screen. Paste
   it into the internal email and you're done.

## Deploy with the command line (alternative)

```bash
git init
git add index.html .nojekyll README.md
git commit -m "FOG diagnostic — initial"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

Then enable Pages as in step 3 above.

## Preview locally

Open `index.html` in any browser — double-click works. Or serve it:

```bash
python3 -m http.server 8000   # then visit http://localhost:8000
```

## Custom domain (optional)

To serve it from something like `fog.vancap.com`, add a file named `CNAME`
containing that hostname, then point a CNAME DNS record at
`<your-username>.github.io`. GitHub's Pages settings walk through the rest.

---

## How to customize

Everything lives in `index.html`. Three places worth knowing:

**Brand.** The color system is at the top of the `<style>` block in `:root`
(`--navy`, `--gold`, `--paper`, etc.). Change them there and the whole tool follows.

**The ladder.** The five postures and the build-out each one starts at live in the
`presets` object in the `<script>` (e.g. `none: {build:0}`, `inhouse: {build:78}`).
The order and labels of the ranked ladder live in the `LADDER` array just below it.

**The benchmarks.** The captive ceiling assumptions — attach rate, finance spread,
retained-customer uplift, dealer diversion, and the net-new-sales sensitivity lever —
are the slider defaults inside the "math, itemized" drawer and the `compute()`
function. Move a default in the markup, or let the prospect move it live.

## The engine, in one line

```
FOG = captive ceiling × (1 − build-out)
```

The ceiling is the full annual economics a built captive delivers for a business of
that size — finance income, retained-customer revenue, net-new sales margin, and
dealer volume held. It does not change with posture. Build-out is how much of that a
prospect has already put in place. The gap is the rest. Widest at "nothing formal,"
narrowest at "in-house" — by construction.

---

*Virtual Captive™ is a managed finance program of Vanguard Captive Management.
This tool and its contents are proprietary to VCM. Figures are directional estimates
for discussion, not an offer of credit.*
