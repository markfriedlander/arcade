# Arcade

A small room of quiet browser games. No ads, no accounts, no timers, nothing to install.

**Play: [markfriedlander.github.io/arcade](https://markfriedlander.github.io/arcade/)**

## Games

| Game | | |
|---|---|---|
| [Bubbles](https://markfriedlander.github.io/arcade/bubbles/) | A bubble shooter with no fail state | playable |
| Killer Sudoku | Cages and sums, no given digits | in the works |

## How it is built

Every game is a single self-contained HTML file. No build step, no bundler, no
package manager, no dependencies, and no network calls at run time. Open the
file and it runs, including from `file://` and including offline.

```
index.html          the arcade landing page
bubbles/index.html  Bubbles, entire
LICENSE             MIT
```

Scores and saved boards are kept in the browser's own `localStorage`, on the
player's device. Nothing is collected and nothing is sent anywhere.

## Running it locally

Open `index.html` in a browser. That is the whole procedure.

`localStorage` is restricted on `file://` in some browsers, so saving may not
work that way. If you want that, serve the folder over HTTP:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Adding a game

Drop a self-contained `index.html` into a new folder, then add a card to the
`.games` grid on the landing page. Keep to the house rules: no dependencies,
no network, works on touch and mouse, and no way to make the player feel bad
about putting it down.

## Notes on Bubbles

The aim preview and the live shot run through one shared marching function in
fixed increments, so the dotted line and the ghost ring always agree with where
the bubble actually lands, at any frame rate.

There is no game over. When the board reaches the line, the bottom row dissolves
instead of ending the run.

Levels are optional and add no fail state, only a sense of progress. A "line" is
a full row's worth of bubbles cleared by the player's own shots, so the bar moves
whenever something pops. Bubbles the tide takes away do not count. Level one costs
X lines and each level after it costs Y more, both adjustable in the menu.

## License

MIT. See [LICENSE](LICENSE).
