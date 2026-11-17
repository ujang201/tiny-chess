# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/ujang201/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/ujang201/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

TINYCHESS — a chess engine in 4 KB of Python: 0x88 board, alpha-beta with quiescence search, transposition table, killer moves, material + piece-square evaluation, fixed 50,000-node search per move. It plays the house gauntlet through the env at MAKEFUN_ENV_URL.

## Run it

```sh
python3 main.py
```

## Verification

- `main.py` is the kit-packed entrypoint: `makefun compress main_readable.py --out main.py` gives 3,284 bytes (cap 4,096); the readable source is 8,321 bytes / 402 lines and is shipped beside the entry, not committed.
- Perft: startpos depths 1–4 = 20, 400, 8902, 197281; Kiwipete depths 1–3 = 48, 2039, 97862. Move generation checked against python-chess on 15 random games: 0 mismatches. Depth-3 search agrees with the reference engine on 5 test positions (same best move and score).
- Determinism: two separate processes pick identical root moves on 3 test positions (b1c3, a1b1, b1c3).
- Mock-env smoke test (trial 0, 240 s window): game 1 win by mate vs depth-2, game 2 draw by repetition vs depth-3; the 240 s timeout cut the trial short afterwards (exit 124), protocol confirmed working end to end.

---

<sub>Entered on [make.fun](https://make.fun/?ref=wfjv7kgb&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
