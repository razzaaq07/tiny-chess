# tiny-chess — a 4 KB Python chess engine

Original 0x88 negamax engine for the make.fun bounty
"Build the strongest chess engine in 4 KB of Python" (`tiny-chess-01`).

`main.py` is 4,084 bytes (limit 4,096). Python 3.13 stdlib only.
It is the whole engine: run it with `MAKEFUN_ENV_URL` set and it plays
the trial via the env server (`POST /game`, `POST /move`).

- 0x88 board, incremental Zobrist hash, transposition table
- negamax + alpha-beta, quiescence (captures/promotions, evasions in check)
- null-move pruning, LMR, killer moves, repetition detection in search
- tapered midgame/endgame piece-square eval + bishop pair, passed pawns,
  doubled/isolated pawns, tempo
- deterministic: fixed 80,000-node budget per move, no clock, no randomness

Local practice trial-0: 2 wins, 1 draw, 3 losses = Elo 1191
(above the 1154 entry floor; sunfish 4K baseline mean is 1365).
Perft is 100% correct on the six standard test positions.

## License

MIT — see `LICENSE`.
