# Growing Garden

A single-page website that grows over time: one new flower appears for every week of a relationship, and a tree made of animated hearts stands beside a live counter of how long the couple have been together.

**Live site:** https://jlk31.github.io/growing-garden/

## Brief Description

Growing Garden is a personal gift built as a web page instead of a card. The top of the page is a garden that gains a flower each week. Scrolling down moves the sky from daytime to night and reveals a heart-shaped tree, with a counter showing the years, months, days, hours, minutes and seconds since the relationship began.

The whole project is one HTML file with no build step, no frameworks and no external requests. It was kept that small on purpose: it loads instantly on a phone, works offline once opened, and can be hosted for free on GitHub Pages.

## Tech Stack

| Area | Choice | Why |
|---|---|---|
| Structure | HTML5 | One file, readable top to bottom |
| Styling and animation | CSS (flexbox, grid, keyframes) | Animations run in the browser's own engine, so no animation library is needed |
| Graphics | Inline SVG | Flowers and hearts stay sharp at any screen size and are drawn once, then reused |
| Logic | Vanilla JavaScript | Under 100 lines; a framework would add weight without adding anything |
| Hosting | GitHub Pages | Free static hosting straight from this repository |

## Features

- **A garden that grows.** The number of flowers is calculated from the start date, so a new one appears each week without the page ever being edited.
- **A stable garden.** Flower shapes, colours and sizes come from a seeded random number generator, so the garden looks the same on every visit and only ever gains flowers.
- **A heart tree.** 170 hearts in seven colours are placed inside a mathematical heart curve, so the canopy is itself heart-shaped. Each heart pulses at its own speed.
- **A live counter.** Years, months and days are calculated on the calendar (accounting for month lengths, leap years and clock changes), and the clock ticks every second.
- **Phone and laptop layouts.** The tree and counter sit side by side on wide screens and stack on narrow ones.
- **Accessibility.** Animations switch off for visitors who have asked their device to reduce motion, and the graphics carry text descriptions for screen readers.
- **Private by default.** The page asks search engines not to index it and contains no names or photos.

## Installation Steps

No dependencies or build tools are needed.

1. Clone the repository:
   ```bash
   git clone https://github.com/jlk31/growing-garden.git
   cd growing-garden
   ```
2. Open `index.html` in any modern browser.

## Usage Examples

### Set your own date

Open `index.html` and edit the two values at the top of the `<script>` block:

```js
const START = '2026-07-03';   // the day you got together, as YYYY-MM-DD
const HEARTS = 170;           // how many hearts make up the tree
```

The headings and the short messages are plain text in the HTML and can be changed in the same file.

### Publish it with GitHub Pages

1. On GitHub, open the repository's **Settings**, then **Pages**.
2. Under **Build and deployment**, choose **Deploy from a branch**.
3. Select the `main` branch and the `/ (root)` folder, then save.
4. After a minute or so the site is live at `https://<username>.github.io/growing-garden/`.

### Run the self-check

The date calculation has a built-in check covering anniversaries, month ends, leap days and clock changes. Open the page with `#test` on the end of the address and look at the browser console:

```
index.html#test
```

`Self-check finished` with nothing above it means every case passed.

## How It Works

| Part | Approach |
|---|---|
| Flower count | Total days together, divided by seven, plus one for the flower planted on day one |
| Heart canopy | Random points are generated and kept only if they fall inside the heart curve `(x² + y² − 1)³ − x²y³ ≤ 0` |
| Calendar gap | Steps forward in whole months from the start date, then counts the leftover days, so "1 month" is always a calendar month |

## Future Roadmap

- A short message attached to individual flowers, shown when one is tapped.
- Special flowers on anniversaries and birthdays.
- Hearts that occasionally drift down from the tree.
- An "add to home screen" icon so the page opens like an app on a phone.

## Licence

Released under the [MIT Licence](LICENSE).
