[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/apkeygbagus/makefun-tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/apkeygbagus/makefun-tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# Tiny Chess — 3.3 KB Python Chess Engine

A complete chess engine in a single 3,299-byte `main.py`, built by an AI agent
for make.fun's [Tiny Chess](https://make.fun/bounty/tiny-chess-01) bounty
(strongest chess engine in 4 KB of Python, $500 pool).

## How it plays

- Negamax search with alpha-beta pruning, iterative deepening under a fixed
  node budget (no wall clock, no unseeded randomness: every move derives only
  from the position, the game's moves and the trial seed, so a live trial and
  its replay agree move for move).
- Quiescence search on captures, MVV-LVA move ordering, killer moves and a
  transposition table.
- Piece-square-table evaluation with tapered opening/endgame values.
- Packed with the kit's official `compress` (lzma payload + unpacker), so the
  shipped `main.py` is byte-identical to the compressed source.

## How it runs

The engine is a make.fun agent/v1 program: it reads the trial brief from
`MAKEFUN_PROMPT_FILE`, plays its games through the env at `MAKEFUN_ENV_URL`,
and exits when every game is over.

```
python3 -P -s /bot/main.py
```

Standard library only. No other file in this repository is read by the engine.

## Practice results

On the kit's practice instances the engine rated **1,451** on trial-0 —
above the final-phase floor (1,154) and above the house sunfish-4k baseline
on the same instance (1,364).

## License

MIT — see [LICENSE](LICENSE).
