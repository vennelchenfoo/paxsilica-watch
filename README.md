# Pax Silica Watch

A free, static campaign site documenting the impact of the Pax Silica Economic
Security Zone (New Clark City, Tarlac, Philippines): affected communities,
livelihoods, environment, the global supply chain, and the petition to stop it.

**Everything is ONE file:** `index.html`. Open it in any browser and it works —
no build step, no server, no dependencies to install.

---

## Publish on GitHub Pages (free, ~5 minutes)

1. **Create the repository:** github.com → **+** → **New repository** →
   name it `paxsilica-watch` → set **Public** → **Create repository**
2. **Upload:** click **Add file → Upload files** → drag in `index.html` and
   `README.md` → **Commit changes**
3. **Enable Pages:** repo **Settings → Pages** → Source: **Deploy from a branch** →
   Branch `main`, folder `/ (root)` → **Save**
4. Wait 1–2 minutes. Live at: `https://YOUR-USERNAME.github.io/paxsilica-watch/`

Optional: point a custom domain in **Settings → Pages → Custom domain**.

---

## How to UPDATE the site

All content lives in one clearly marked block near the bottom of `index.html`:

```
╔══════════════════════════════════════════════════╗
║  EDITABLE DATA BLOCK — all site content below     ║
╚══════════════════════════════════════════════════╝
const SITE_DATA = { ... }
```

Edit ONLY inside that block. You can do it on github.com: open `index.html` →
pencil icon → edit → **Commit changes**. The live site refreshes in ~1 minute.

### Recipes

**New investor named** → add a row to the `companies` array:
```js
{ name: "Nvidia", country: "USA", role: "Anchor tenant — AI data center",
  commitment: "$X billion announced 2026-08-01", status: "CONFIRMED" },
```

**Exact community / boundary confirmed** → edit the matching `areas` entry
(`lat`, `lng`, `radiusMeters`, add to `barangays` / `communities`). The map
redraws automatically.

**New mineral or product confirmed** → edit the relevant `supplyChain` stage
(or add a stage — the value-ladder chart adapts).

**Something happens** → add to `timeline`:
```js
{ date: "2026-09-15", event: "Supplemental Agreement signed; text published.",
  status: "CONFIRMED" },
```

**A claim's status changes** → flip the `status` field. Valid values:
`"CONFIRMED"`, `"ALLEGED"`, `"CONTESTED"` — badges restyle themselves.

**After every update:** set `meta.lastUpdated` to today's date (shown in the
hero and footer so readers can trust the page's freshness).

### Safety
- Keep the comma after each `{ ... },` entry
- If the page shows a rust-colored "Render error" banner after an edit, there's a
  syntax slip in the data block — fix it or revert the commit (**History → ⟲**)
- The page never goes blank: the map and renderer are guarded, and errors are
  shown on screen with the reason

---

## Letting others contribute
- **Settings → Collaborators** to add trusted editors, or
- Keep it open: others fork → edit → open a **Pull Request**; you review and merge.
  Nothing goes live without your approval.
- Enable **Issues** so readers can submit corrections with sources.

## Notes
- Map: Leaflet + CARTO dark basemap (free with attribution kept).
- Petition: embedded via Google Forms' official embed URL. If ILPS moves it,
  update `meta.petitionUrl` and `meta.petitionEmbedUrl` in the data block.
