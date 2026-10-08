# Growing Garden

An interactive one-page gift: a single tap grows a tree whose leaves are hearts, a flower blooms beneath it for every week of the relationship, and a live counter and handwritten-style letter sit beside it.

**Live site:** https://jlk31.github.io/growing-garden/

## Brief Description

Growing Garden is a personal gift built as a web page instead of a card. It opens on a single pulsing heart. Tapping it plays a short animated sequence: "I love you" appears, a seed falls to the ground, a trunk rises and branches out, and around 240 hearts blossom into a heart-shaped canopy. A counter then shows exactly how long the couple have been together, and a "Letter" button opens a note that types itself out.

The whole project is one HTML file with no build step, no frameworks and no external requests. It loads instantly on a phone, and is hosted for free on GitHub Pages.

## Tech Stack

| Area | Choice | Why |
|---|---|---|
| Structure | HTML5, including the native `<dialog>` element | The letter pop-up gets focus handling, the Escape key and a dimmed backdrop from the browser, with no modal library |
| Styling and animation | CSS keyframes | The entire intro sequence is timed in CSS; JavaScript only starts it with one class |
| Graphics | Inline SVG | Hearts, flowers and the tree stay sharp at any screen size and are drawn once, then reused |
| Logic | Vanilla JavaScript | Under 150 lines; a framework would add weight without adding anything |
| Hosting | GitHub Pages | Free static hosting straight from this repository |

## Features

- **Tap-to-start intro.** The page waits on a single heart so the animation plays when she is ready, not while the page is still loading.
- **A growing tree.** The trunk rises, branches draw themselves on, and hearts pop in from the middle of the tree outwards.
- **A heart-shaped canopy.** Hearts are placed inside a mathematical heart curve, so the canopy itself forms a heart.
- **A meadow that grows over time.** One flower is planted along the ground for every week together. Flower positions are seeded, so existing flowers never move when a new one appears.
- **A live counter.** Days, hours, minutes and seconds since the start date, ticking every second.
- **A self-typing letter.** The letter types itself out the first time it is opened, then stays fully written if she closes and reopens it.
- **Falling petals.** Hearts drift slowly down from the tree once it has grown.
- **Phone and laptop layouts.** On a phone the counter sits above the tree; on a wide screen the tree slides right and the counter sits beside it.
- **Accessibility.** Visitors whose device is set to reduce motion skip straight to the finished scene, and the graphics carry text descriptions for screen readers.
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

### Set the date and write the letter

Open `index.html` and edit the two values at the top of the `<script>` block:

```js
const START = '2026-07-03';   // the day you got together, as YYYY-MM-DD
const LETTER = `Hi, my love...

...`;
```

Line breaks inside `LETTER` appear in the letter exactly as written.

### Publish it with GitHub Pages

1. On GitHub, open the repository's **Settings**, then **Pages**.
2. Under **Build and deployment**, choose **Deploy from a branch**.
3. Select the `main` branch and the `/ (root)` folder, then save.
4. After a minute or so the site is live at `https://<username>.github.io/growing-garden/`.

### Run the self-check

The day count has a built-in check covering clock changes and leap years. Open the page with `#test` on the end of the address and look at the browser console:

```
index.html#test
```

`Self-check finished` with nothing above it means every case passed.

## How It Works

| Part | Approach |
|---|---|
| Intro sequence | Every step has a fixed CSS delay and waits for a `go` class on the page; tapping the heart adds that class |
| Heart canopy | Random points are generated and kept only if they fall inside the heart curve `(x² + y² − 1)³ − x²y³ ≤ 0`, then sorted by distance from the centre so the tree blossoms outwards |
| Same tree every visit | A seeded random number generator (mulberry32) replaces `Math.random()` for the tree and meadow |
| Day count | Whole calendar days between midnight on the start date and today, rounded so the 23- and 25-hour days around clock changes do not skew it |

## Future Roadmap

- A photo carousel inside the letter.
- Optional background music with a play/pause button.
- A custom domain.
- Special flowers on anniversaries and birthdays.

## Licence

Released under the [MIT Licence](LICENSE).
