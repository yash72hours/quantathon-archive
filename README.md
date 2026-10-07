# Quantathon Archive

Past Quantathon papers from Finance Club, IIT Roorkee (2020 to 2026), tagged by year and topic. Every one of the 63 problems has a hint and a worked solution.

**Live site:** https://quantathonarchive.netlify.app/

## How the site works

The site is `index.html` plus a small `assets/` folder holding the tab icons and the link-preview image. There is no build step: Netlify serves the files exactly as they are in the repo, and every push to the `main` branch is deployed automatically.

## Sharing a filtered view

Filters are kept in the address bar, so copying the link reproduces the view:

| Link ending | Shows |
|---|---|
| `?year=2023` | the 2023 paper |
| `?topic=prob` | every probability problem |
| `?topic=prob&year=2023` | probability problems from 2023 |
| `?q=dice` | problems whose statement mentions "dice" |
| `?group=topic` | the list grouped by topic instead of by year |
| `#q-2024-5` | 2024 Q5 on its own (if active filters would hide it, they are cleared) |

Topic codes are listed under "Editing or adding a problem" below. "Hide solved" is a personal setting, so it is remembered in the browser rather than put in the link.

## Editing or adding a problem

Each problem is an `<article>` block inside `<div id="pool">`:

```html
<article class="q" data-paper="2023" data-topic="prob" data-num="3">
  <h3>Jackpot</h3>
  <p>Problem statement goes here.</p>
  <details class="hint"><summary>Hint</summary><div class="dd">
    <p>A short nudge.</p>
  </div></details>
  <details class="sol"><summary>Detailed solution</summary><div class="dd">
    <p class="ans"><b>Answer.</b> The final answer.</p>
    <p>The full working.</p>
  </div></details>
</article>
```

- `data-paper` is the year. It must match an `id` in the `PAPERS` list in the script at the bottom of the file.
- `data-topic` is one of: `prob`, `decide`, `walk`, `comb`, `game`, `logic`, `geo`, `opt`, `fx`, `tvm`, `arb`, `port`, `mkt` (names and colours are in the `TOPICS` list).
- `data-num` is the question number within that year. Keep numbers unique per year.
- Background passages go in `<details class="ctx"><summary>Background passage</summary>...</details>`.
- Editorial notes (a clarified reading, a suspected typo) go in `<p class="ed-note">...</p>` and show with a gold rule.
- The hint and solution blocks are optional. Leave them out until a solution has been checked.

### Writing maths

- Inline maths: `\( ... \)`. Display maths: `\[ ... \]`. Rendering is done by KaTeX.
- Don't use `$...$` for maths; dollar signs are treated as ordinary text (for prices).
- Inside HTML, write `<` as `&lt;`, `>` as `&gt;` and `&` as `&amp;`, including inside formulas.
- Maths inside hints and solutions is rendered the first time a reader opens them, which keeps the page fast on phones. When checking a new solution, open its hint and solution panels to see the maths.

## Adding a new year

1. Add an entry to `PAPERS` in the script, for example `{ id: "2027", year: "2027", round: "", chip: "2027" }`.
2. Add that year's problems as `<article>` blocks with `data-paper="2027"`.

The coverage grid, filters, link options and counts update automatically. The total "63 problems" and the year range are written out in a few places that need a manual update: the intro paragraph (`id="lede"`), the `description` and `og:description` meta tags, and the preview image `assets/og-image.png`.

## Contributing

1. Create a branch and edit `index.html`.
2. Open the file in a browser to check that it renders and the maths displays, including inside the hint and solution panels.
3. Open a pull request. Once it is merged into `main`, Netlify deploys it within a minute or two.
