# Quantathon Archive

Past Quantathon papers from Finance Club, IIT Roorkee (2020 to 2026), tagged by year and topic, with hints and worked solutions.

**Live site:** https://quantathonarchive.netlify.app/

## How the site works

The whole site is one file, `index.html`. There is no build step: Netlify serves the file exactly as it is in the repo, and every push to the `main` branch is deployed automatically.

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
- The hint and solution blocks are optional. Leave them out until a solution has been checked.

### Writing maths

- Inline maths: `\( ... \)`. Display maths: `\[ ... \]`. Rendering is done by KaTeX.
- Don't use `$...$` for maths; dollar signs are treated as ordinary text (for prices).
- Inside HTML, write `<` as `&lt;`, `>` as `&gt;` and `&` as `&amp;`, including inside formulas.

## Adding a new year

1. Add an entry to `PAPERS` in the script, for example `{ id: "2027", year: "2027", round: "", chip: "2027" }`.
2. Add that year's problems as `<article>` blocks with `data-paper="2027"`.

The coverage grid, filters and counts update automatically.

## Contributing

1. Create a branch and edit `index.html`.
2. Open the file in a browser to check that it renders and the maths displays.
3. Open a pull request. Once it is merged into `main`, Netlify deploys it within a minute or two.

## Problems still without solutions

- 2023: Grid Conundrum, Seed-y Grid Puzzle
- 2024: Financial World
- 2025: Let's Play Pebbles!, Infinite Arrays
