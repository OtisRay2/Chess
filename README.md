# Chess

A fully-featured chess game playable in the browser, deployed via GitHub Pages.

## Play

**[Play online →](https://otisray2.github.io/Chess/)**

## Features

- **Full chess rules** — castling, en passant, pawn promotion, check, checkmate, stalemate
- **Bot opponent** — minimax engine with alpha-beta pruning and piece-square tables (3-ply lookahead)
- **Two modes** — 2 Player (local) or vs Bot (you play White, bot plays Black)
- **Move hints** — click a piece to see legal moves highlighted on the board
- **Last-move highlight** — previous move always visible
- **Undo** — steps back one full turn (two plies in bot mode so it's always your move)
- **Captured pieces** display for both sides
- **Mobile friendly** — responsive board that fits any screen, touch-optimised with no tap delay

## Controls

| Action | How |
|--------|-----|
| Select piece | Tap / click it |
| Move piece | Tap / click the highlighted destination square |
| Deselect | Tap the same piece again, or tap an empty square |
| Promote pawn | Reach the back rank — a piece picker appears |
| Undo | **Undo** button |
| New game | **New Game** button |
| Switch mode | **2 Player** / **vs Bot** toggle |

## Deployment

The site deploys automatically to GitHub Pages on every push via GitHub Actions.

### Enable GitHub Pages

1. Go to **Settings → Pages** in the repository
2. Set **Source** to **GitHub Actions**
3. Push to the branch — the workflow runs and the game goes live

### Workflow

`.github/workflows/deploy.yml` uploads the repository root as the Pages artifact and deploys it with `actions/deploy-pages`.

## Local development

No build step required — open `index.html` directly in a browser.

```sh
open index.html   # macOS
xdg-open index.html  # Linux
```

## Bot details

The bot uses **minimax with alpha-beta pruning** at depth 3. Positions are scored with:

- **Material** — standard piece values (P=100, N=320, B=330, R=500, Q=900)
- **Piece-square tables** — bonuses/penalties for piece placement (centre control, king safety, pawn structure)

The bot always promotes to a queen and shuffles equal-scored moves for variety.
