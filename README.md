# Exploring Interpretability

At the end of last year, I took on the ambitious project of understanding and replicating (on a much smaller level), Monosemanticity through Anthropic's research [paper](https://transformer-circuits.pub/2023/monosemantic-features/index.html). Since I was very new to the area of research and had no access to 
textbooks or other guides, I decided to create my own visual guide!

## Files

- `index.html` — the hub / landing page ("Exploring Interpretability", 4 paths)
- `latent-space.html` — Path 01: Visualizing Latent Space
- `seeing-inside-the-black-box.html` — earlier single-page prototype (safe to delete)

Keep `index.html` and `latent-space.html` in the same folder — they link to each other.

## Editing text

Open either `.html` file in any text editor (VS Code, TextEdit, Notepad).
Every file starts with an `✏️ EDITING THIS PAGE` comment that explains what's where.
Rule of thumb: search for the exact words you see on the page and rewrite them.

Things that live in the `<script>` section instead:

- cluster names and hover snippets → the `CLUSTERS` list in `latent-space.html`
- the striped pattern → change `seed` for a new layout, `PAL` for colors

Colors and fonts for the whole page → the `:root` block at the top of `<style>`.

## Putting it in your portfolio

The pages are plain static HTML — no build step, no server. Any static host works:

**Easiest — Netlify Drop.** Go to https://app.netlify.com/drop and drag this whole
folder onto the page. You get a live URL in seconds (free account to keep it).

**Most portfolio-standard — GitHub Pages.**
1. Create a repo (e.g. `exploring-interpretability`) on github.com
2. Upload `index.html`, `latent-space.html`, and this README
3. Repo Settings → Pages → Source: `main` branch → Save
4. Live at `https://<your-username>.github.io/exploring-interpretability/`

**Also fine:** Vercel, Cloudflare Pages, or dropping the folder into any web host.
If you already have a portfolio site, upload the folder as a subdirectory and link
to `/exploring-interpretability/` from your projects page.

Notes:
- Fonts (Clash Display, General Sans, Space Mono) load from CDNs — they need
  internet, which is fine once hosted. Everything else is self-contained.
- The pages work offline too; you just get fallback fonts.

## Credits worth keeping on the page

Built on Anthropic's papers at transformer-circuits.pub. Examples are paraphrased
for teaching; the numbers (512 neurons, 4,096 features, 1M/4M/34M) are from the papers.
