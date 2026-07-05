# Exploring Interpretability — handoff notes

Project: interactive visual guide to Anthropic's interpretability research, for Ruth's
portfolio. Audience: people who don't know much about AI. Editorial Bauhaus design.
**Read this whole file before touching anything.**

## Current state (all working, verified)

- `index.html` — hub. Title "EXPLORING INTERPRETABILITY", generative striped-pixel hero,
  4 path cards. Path 01 live; 02/03/04 marked "in the works".
- `latent-space.html` — Path 01 "VISUALIZING LATENT SPACE", COMPLETE. 5 scenes:
  1. draggable 3D point cloud (7 clusters, hover tooltips) + "you're looking at a shadow"
     aside (spinning cube → 2D shadow = projection honesty)
  2. distance = meaning: click a sentence → point flies in, shows 4 nearest neighbors;
     the two "bank" sentences land in different clusters (river→nature, loan→money)
  3. direction = meaning: animated analogy parallelogram (man→king :: woman→queen;
     tense; capitals) + slider walking a sentence along the "French" direction
  4. human concepts vs model's: 3-slider concept mixer (cat/French/formal) → dot in
     axis cube + sentence at that location; "concept = dial, not box"
  5. the catch: slider crowds 2→12 concept arrows into 2D, crosstalk grows →
     cliffhanger into Path 02
- `seeing-inside-the-black-box.html` — EARLIER PROTOTYPE (dark theme, 12 sections,
  different design). Superseded, but MINE IT for Paths 02–04 content: it has working
  superposition slider, SAE diagram, feature browser, clamp demo, Golden Gate dial,
  safety dashboard. Delete before publishing.
- `README.md` — user-facing: how to edit text, how to publish (Netlify Drop / GitHub Pages).

## Design system (do not drift from this)

- Palette (from user's cover artwork): paper `#f0e7d5`, panel `#f5eee0`, ink `#16141b`,
  red `#e3242f`, maroon `#8c2033`, blue `#3961c6`, yellow `#eda211`, green `#23784f`,
  pink `#e995ad`, light blue `#5b86d6`, muted `#6d675a`.
- Fonts (CDN): Clash Display (Fontshare) = display, BOLD CAPS headlines with one
  outlined word (`.o` class, -webkit-text-stroke); General Sans = body;
  Space Mono (Google) = ALL metadata/labels/buttons/readouts.
- Chrome per page: topbar wordmark "Exploring Interpretability." + mono nav →
  3px blackrule → mono meta strip (PATH / SERIES / SUBJECT / READ) → framed
  generative striped-pixel banner (seeded, palette above) → kicker → giant caps H1.
- Panels: sharp corners, 2.5–3px ink borders. Buttons: mono, ink border,
  yellow hover, ink-filled when active. Hover cards: translate(-4,-4) + 6px ink shadow.
- Each scene: numbered scenebar chip, H2 in caps, intro prose, interactive stage,
  centered `.note` with yellow-highlighted key phrase.
- User requirement: distinctive fonts, bold caps titles, "way better design than
  default AI" — she rejects generic. She gives design feedback; ITERATE WITH HER,
  one scene at a time. Don't one-shot big builds; she wants to be asked for opinions.

## Content plan (agreed arc, next steps)

- Path 02 SUPERPOSITION (next): why crosstalk is tolerated. Toy-model story:
  sparsity slider → 5 features in 2D snap from 2-orthogonal → antipodal pairs →
  pentagon (phase change); polysemantic neurons as the visible symptom; ReLU noise
  clipping. Source: Toy Models of Superposition (2022). Prototype has a working
  pentagon widget to upgrade to house style.
- Path 03 MONOSEMANTICITY: SAE untangling (512 neurons → 4,096 features),
  feature browser (Arabic script / DNA / base64 features), causality (clamp feature →
  model outputs that thing). Source: Towards Monosemanticity (2023).
- Path 04 STEERING & SAFETY: scaling to Claude 3 Sonnet (1M/4M/34M features,
  multilingual+multimodal), Golden Gate Claude dial, safety features (deception,
  sycophancy, unsafe code), honest caveats. Source: Scaling Monosemanticity (2024).
- When a path goes live: in `index.html` change its card `<div class="path soon">`
  to `<a class="path" href="file.html">`, status chip to "● Live".

## Conventions & gotchas

- Everything self-contained per page (no build step, no libraries); canvas/SVG + vanilla JS.
- All copy is inline HTML — ✏️ editing comment at top of each file explains what's
  where. User edits text herself; preserve her edits (diff before rewriting!).
- Editable data lives in clearly named JS consts: CLUSTERS, DROPS, ANALOGIES, MORPH,
  COMBOS, PAL. Seeded RNG (LCG 16807) everywhere for reproducible patterns.
- transformer-circuits.pub pages TIME OUT on direct fetch — use arXiv mirrors,
  web search, or Claude-in-Chrome for verification.
- Verify before presenting: extract <script> (strip HTML comments first — the ✏️
  comment contains the literal string `<script>` and breaks naive regex),
  `node --check`, then jsdom smoke test with canvas getContext stubbed
  (Proxy returning no-ops) and requestAnimationFrame → setTimeout.
- Facts kept accurate: 512 neurons / 4,096 features; 1M/4M/34M dictionaries;
  Golden Gate feature multilingual+multimodal; safety-relevant feature families.
  Cloud/cluster data is ILLUSTRATIVE (footer says so — keep that honesty).

## Immediate TODOs

1. User was asked to review Path 01 scenes as a beginner (wording/pacing) — collect
   her edits/reactions first.
2. Build Path 02 in house style (one scene at a time, ask opinions between).
3. She may attach her cover artwork as a real file — if so, swap generated hero
   on index.html for the image (keep generated banner on inner pages).
4. Delete `seeing-inside-the-black-box.html` before publishing.
