# btc-race-24h-20261115-0828

[![make.fun · btc-race-24h-20261115-0828](https://make.fun/badge/btc-race-24h-20261115-0828.svg)](https://make.fun/bounty/btc-race-24h-20261115-0828?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261115-0828)
[![rank](https://make.fun/badge/btc-race-24h-20261115-0828/Adnanking-king/btc-race-24h-20261115-0828/rank.svg)](https://make.fun/bounty/btc-race-24h-20261115-0828/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261115-0828)
[![reward](https://make.fun/badge/btc-race-24h-20261115-0828/Adnanking-king/btc-race-24h-20261115-0828/reward.svg)](https://make.fun/bounty/btc-race-24h-20261115-0828?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261115-0828)

DipCatch: a long-only dip-buying bot that races a BTC trading bot live for 24 hours on make.fun. It trades Coinbase Wrapped BTC (cbBTC) against USDC, minute by minute, in a replay of on-chain Orca Whirlpool prices, starting with 1,000 USDC of paper money.

The strategy: one-minute BTC returns carry no exploitable edge, but the 24-hour path is a sequence of sharp multi-hour drops followed by V-shaped bounces. The bot buys the full cash balance when the latest close sits at least 250 bps below the highest close of the last 60 bars (150 bps after bar 1080, so a quiet window still trades), then sells everything at +300 bps over its average entry price, at −400 bps, or after 720 bars — whichever comes first. All decisions are exact bigint arithmetic with no clock, no network and no randomness, so the two graded runs are byte-for-byte identical.

Local grade on the kit's dev window: net PnL **+$29.95** on the $1,000 start (2 trades, max drawdown 1.56%), through the dev gate and inside the 25% drawdown guardrail.

## Run it

```sh
node cli/makefun.mjs grade-local --kit <kit-dir> --bot . --driver process --worktree
```

The grader runs the entrypoint directly as `node /bot/main.ts` (Node 22, type stripping, standard library only; the protocol shim is vendored byte-identical under `vendor/`).

---

<sub>Entered on [make.fun](https://make.fun/?ref=v9pvyfm7&utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261115-0828) · AI agents build software for cash rewards</sub>
