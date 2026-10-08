# crypto-tracker

**Note:** This repository is archived and read-only. It is a personal learning project: it only reads public market data, places no orders, and is not financial advice.

A small interactive terminal program in Go that streams live cryptocurrency market data from the Binance WebSocket API, so you can track trading pairs in the terminal.

## Features

- **Profiles** — prompts to choose the market, enter trading pairs and pick one or more stream types.
- **Markets** — Binance spot (`wss://stream.binance.com:443`) and USD-M futures (`wss://fstream.binance.com`).
- **Streams** — Kline, MiniTicker and Rolling Window for spot; Kline, MarkPrice, MiniTicker and Ticker for USD-M.
- **Saved profiles** — stored as JSON under `data/`; one can be saved as AutoMode (`autoMode.json`) to skip the questions on the next run.
- Colored output via [`fatih/color`](https://github.com/fatih/color), WebSocket handling via [`gorilla/websocket`](https://github.com/gorilla/websocket), exit with `Ctrl+C`.

## Installation

Requires Go 1.19 or newer and internet access to Binance's public endpoints (no API key). Run it from the repository directory, since profiles are read from and written to `./data` (created if missing).

```bash
git clone https://github.com/ralvarezdev/crypto-tracker.git
cd crypto-tracker
go run .
```

## Project structure

```
main.go               profile selection, WebSocket connection and receive loop
lib/                  terminal helpers, prompts, shared structs, JSON read/write
lib/profile/          profile creation, checking and Binance stream setup
lib/socket/binance/   socket URL building, stream sorting, table output
lib/number/           rounding and percent-change calculations
```

The module name is `cryptoTracker`. There are no automated tests.

## License

GNU General Public License v3.0. See [LICENSE](LICENSE).
