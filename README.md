# UWED talk (reveal.js)

"Scaling Intelligence Under Resource Constraints: Measurement and Optimization for Sustainable Computing": 53 slides (one more is skipped with data-visibility="hidden").

- Introduction (slides 1–21): `public/orig/intro-*.jpg`, from slides 1–17 of `Pengfei_U-WED_slides.pptx`,
  plus two HTML cooling slides after intro slide 11 (heat path, and PUE/WUE by cooling method from
  Microsoft Azure "Modern Datacenter Cooling" and LBNL 2024 Fig. 4.4). Slide 6 (training energy of
  2025 open-weight models; * = estimated carbon/water) and slide 7 (inference vs. agents) are HTML;
  intro slide 15 is split into two pages (diagram, then offsite/onsite photos).
- Water section (slides 22–34): the new 13-slide "Small Bottle, Big Pipe" section, built as HTML in
  the same visual style (Arial, black titles, grey captions).
- Remaining slides (35–53): `public/orig/slide-*.jpg`, original slides 24–39 of
  `AI_Public_Health_Reorganized .pptx`. Original slide 33 (slide 45 here) is rebuilt in HTML so its
  PUE chart is no longer stretched. Original slide 34 is commented out. Original slide 28 (Omaha news) follows the health quick
  facts, then an HTML slide on the three sources of data-center air pollution (grid plants, backup
  diesel, onsite gas turbines such as xAI in Memphis). Before the eGLB case study,
  three slides cover eGLB: an HTML slide on the fairness-aware GLB objective, then the algorithm and its
  intuition (`public/orig/eglb-*.jpg`, slides 39 and 40 of `2026_AI_public_health.pdf`; their baked-in
  titles are covered by HTML titles).
- Image slides are rendered from PowerPoint's PDF export with their speaker notes; their baked-in
  page numbers were removed. Hidden backup slides are not included.
- Look follows the RIT GCCIS course decks: an HTML title slide (logo from `Week_10.key`, orange
  bracket frame), and on every numbered slide a header built in `src/main.js` with the logo, the section
  progress bar (sections start at slides marked `data-section`) and the page number. Slide content is
  scaled to 92% to make room for the header.
- Footnotes on every slide are HTML (`<p class="src">` in `index.html`, styled in `src/style.css`);
  they were removed from the slide images so all footnotes share one font and size.

## Setup

Node.js lives in the conda env `slides`:

```bash
conda activate slides
npm install
npm run dev        # opens http://localhost:5173
```

## Presenting

| Key | Action |
|---|---|
| `S` | Speaker view (notes, timer, next slide) |
| `F` | Fullscreen |
| `O` / `Esc` | Slide overview |
| `B` | Black screen |

No transitions or build animations; slide 42 keeps the original animated Google GIF.

## Export

- PDF: `npm run pdf` → `slides.pdf` (uses the installed Google Chrome)
- Static site: `npm run build` → `dist/`
- GitHub Pages: every push to `main` runs `.github/workflows/deploy.yml`, which builds and publishes
  `dist/` to the `gh-pages` branch. `npm run deploy` does the same by hand.
  (site: https://lipengfeizju.github.io/water_presentation/)

## Files

- `index.html` – all slides and speaker notes
- `src/style.css` – theme matching the original deck
- `public/orig/` – original slides as images
- `public/figures/` – panels cropped from Han et al. (2026) and the El Paso photo
