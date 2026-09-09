# Cardiothoracic ICU Welcome Packet

Static orientation packet for experienced nurses new to CT surgical critical care.
No build step, no dependencies, no backend.

| File | Purpose |
|---|---|
| `index.html` | **The page people get when they click your link.** Follows the viewer's OS theme. |
| `embed.html` | **Iframe target** (Genially, SharePoint Embed web part). Forces light theme so it doesn't go dark on a light canvas. `?theme=dark` / `?theme=auto` override. |
| `robots.txt` + `noindex` meta on both pages | Keeps the site out of search results. |
| `.nojekyll` | Stops GitHub Pages running Jekyll over the files. |

---

## Deploy to GitHub Pages

No Actions workflow needed — unlike the ZOLL simulator, this is plain static
HTML with no build, no client-side routing, no base-path handling, and no
SPA 404 fallback. Publish the branch root directly.

```bash
cd ctsurg-packet-pages
git init
git add .
git commit -m "Cardiothoracic ICU welcome packet"
git branch -M main
git remote add origin https://github.com/scottbrickner/ctsurg-packet.git
git push -u origin main
```

Then: repo → **Settings → Pages** → Source: *Deploy from a branch* →
Branch `main`, folder `/ (root)` → **Save**.

Live in a minute or two at:

- **Link to send staff:** `https://scottbrickner.github.io/ctsurg-packet/`
- **Iframe source:** `https://scottbrickner.github.io/ctsurg-packet/embed.html`

### Updating

Replace `index.html` and `embed.html`, commit, push. Pages redeploys itself.

---

## Iframe embed

```html
<iframe src="https://scottbrickner.github.io/ctsurg-packet/embed.html"
        width="100%" height="720" frameborder="0"
        style="border:0;border-radius:8px"
        title="Cardiothoracic ICU Welcome Packet"></iframe>
```

Give it height — the packet is a long document and a short frame turns it into
a peephole. 720px minimum.

---

## What this deploy is and isn't

**It is public.** GitHub Pages has no password option on a personal account, and
a private repo does not make the published site private. The `noindex` meta tag
and `robots.txt` keep it out of search results; they do not keep it off the
internet.

That is why this build is de-identified. No institution, unit, department or
policy numbers appear anywhere in it. There is no PHI. The drip concentrations
are presented as representative of adult CT surgical practice rather than as
anyone's standard, and the page says so in three places.

**Two clinical items remain open** and are flagged on the page rather than
silently resolved:

1. Source documents disagree threefold on the esmolol ceiling
   (300 vs 100 mcg/kg/min).
2. Hydroxocobalamin does not appear on either IV administration standard the
   dosing was transcribed from, though it is stocked.

Worth clearing with pharmacy before this goes to staff.
