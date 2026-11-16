# Tiny Chess — tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/Mansyur0523/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/Mansyur0523/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in 4 KB of Python. `main.py` (3.859 bytes) is the whole
engine: a 0x88 board, pseudo-legal move generation with king-safety
filtering, material + piece-square evaluation with a separate endgame king
table and bishop-pair bonus, and an iterative-deepening alpha-beta search
with a transposition table, killer moves, history heuristic, MVV-LVA
ordering, quiescence search (captures and promotions, all evasions when in
check) with delta pruning, null-move pruning (R=2) and check extensions.
It searches a fixed 200.000 nodes per move — no clock, no unseeded
randomness — so every trial replays move for move. It plays the gauntlet
through the env at `MAKEFUN_ENV_URL` (`/game`, `/move`) and handles
repetition draws from the game history.

Local practice results (kit `grade-local` trial script, 6 games each):

- trial-0: Elo **1545** — 3 won, 3 drawn, 0 lost, 334 spare plies (700 s)
- trial-1: Elo **1654** — 5 won, 0 drawn, 1 lost, 458 spare plies (782 s)
- mean practice Elo: **1599,5** (floor 1154)
