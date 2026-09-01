# 🍜 Alphabet Soup

**Live:** [alphabetsoup.carterpry.com](https://alphabetsoup.carterpry.com) ([alphabetsoup.pages.dev](https://alphabetsoup.pages.dev))

A bowl of orange broth full of pasta letters you can push around. Built on
[@chenglou/pretext](https://github.com/chenglou/pretext) — text measurement &
layout with zero DOM reflows — everything renders on a single canvas.

## Run it

```sh
python3 -m http.server 8643
# open http://localhost:8643
```

(Any static server works; pretext loads from esm.sh, the Fredoka font from
Google Fonts. If either is unreachable it falls back to canvas `measureText`.)

## Play

| Input | Effect |
|---|---|
| **Drag a letter** | grab it, fling it, watch it splash |
| **Drag empty broth** | stir — nearby letters swirl with your motion |
| **Type a–z** | letters swim up and spell your word in the tray |
| **Backspace** | eat the last letter (drops back into the soup) |
| **Esc** | dump the whole word back in |
| **Space** | splash — scatter everything |

## Where pretext does the work

- `prepareWithSegments` + `measureNaturalWidth` — exact glyph widths for every
  pasta letter: centering, collision radii, and rotated drag hit-boxes.
- Prefix advances of the spelled word (`measureNaturalWidth` on each slice) —
  properly **kerned** tray slots the letters swim into.
- `layoutWithLines` — wraps and centers the HUD tagline on canvas.

No DOM text nodes anywhere; the only element is the `<canvas>`.
