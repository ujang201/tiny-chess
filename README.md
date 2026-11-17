# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/ujang201/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/ujang201/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

TINYCHESS — a chess engine in 4 KB of Python: 0x88 board, alpha-beta with PVS (principal variation search) and quiescence search, transposition table, killer moves + history heuristic, evaluation with material + piece-square tables + pawn structure (isolated/doubled/passed) + king pawn-shield safety, fixed 100,000-node search per move (deterministic, no clock). It plays the house gauntlet through the env at MAKEFUN_ENV_URL.

## Run it

```sh
python3 main.py
```

## Verification

- `main.py` is the kit-packed entrypoint: `makefun compress main_readable.py --out main.py` gives 3,619 bytes (cap 4,096); the readable source is 9,590 bytes and is shipped beside the entry, not committed.
- Perft: startpos depths 1–4 = 20, 400, 8902, 197281; three tricky positions (castling, en passant, promotion) depth 3 = 97862, 2812, 9467 — all exact.
- Determinism: three runs pick identical root moves on two test positions (b1c3, h5f7); the search uses a fixed node budget, no clock, no randomness.
- Practice grading (official kit env + scorer, run locally): trial-0 Elo **1191** (2 won, 1 drawn, 3 lost — beats depth-2 and depth-3 by checkmate, draws depth-4 by repetition; loses to nodes-100k/250k/500k), above the 1,154 practice floor. Trial-1 Elo 876 (0 won, 2 drawn, 4 lost) — the engine is inconsistent across instances/openings (loses to depth-2/3/4 as Black in sharp lines, draws the node rungs by repetition); the round-2 grade runs on trial-0, but the final will need a more consistent engine.
- Worst single move at 100k nodes measured 6.6 s on the slowest sampled middlegame position (limit 10 s); trial-0 wall time 854 s (limit 1,800 s).

---

<sub>Entered on [make.fun](https://make.fun/?ref=wfjv7kgb&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
