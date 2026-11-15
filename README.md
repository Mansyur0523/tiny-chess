[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/Mansyur0523/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/Mansyur0523/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# tiny-chess-01 — 4 KB chess engine

A single-file Python chess engine (stdlib only, no model calls) that
plays the make.fun tiny-chess-01 gauntlet through the env server.

## Engine

- 0x88 board, pseudo-legal move generation + king-safety filter.
- Evaluation: material (P100 N320 B330 R500 Q900) + piece-square
  tables + bishop-pair bonus.
- Search: iterative-deepening alpha-beta with a transposition table,
  killer moves, history heuristic, MVV-LVA capture ordering,
  quiescence search (captures/promotions; all evasions when in check),
  and null-move pruning (R=2, depth >= 3, not in check).
- Deterministic: fixed node budget (100,000 nodes/move), no wall
  clock, no unseeded randomness. Repetition and game-history draws
  handled.
- `main.py` is an LZMA-compressed payload packed with makefun
  compress from the golfed source; the unpacked source is the
  engine above. Total size 3,193 bytes (limit 4,096).

## Local results

- Perft: 18/18 positions correct (startpos, Kiwipete, en-passant,
  promotion and castling cases, depths 1-3).
- Mate/evasion tests: mate-in-1 found, check evasions correct.
- Practice trial-0 (6 games, 1 CPU): 2 wins, 0 draws, 4 losses;
  estimated practice Elo ~1,100. Beats depth-2 and nodes-250k;
  loses to depth-3, depth-4, nodes-100k and nodes-500k.

## Files

- `main.py` — the engine (3,193 bytes).
- `LICENSE` — MIT.
