# Market‑Toolkit

A **batteries‑included** Python helper built from my personal quant‑research scratch‑pad.  It bundles data loading, feature‑engineering, pattern‑detection, and a sprinkle of convenience utilities into a single import — perfect for hack‑weeks, Kaggle comps, or quick employer demos.

---

## ✨ Highlights

| Category            | Goodies                                                                                                   |
| ------------------- | --------------------------------------------------------------------------------------------------------- |
| **Unified loaders** | • Crypto via **ccxt**<br>• Stocks & ETFs via **yfinance**<br>• One‑line CSV archives (CryptoDataDownload) |
| **TA features**     | 140 + indicators from *pandas‑ta* ➕ *pantulipy* behind `add_ta()`                                         |
| **Patterns**        | Double‑tops / double‑bottoms, support‑&‑resistance clustering                                             |
| **Persistence**     | `Path`‑friendly CSV & SQLite helpers                                                                      |
| **Extras**          | Forex‑Factory calendar scraper, Google‑Trends wrapper, day‑of‑week attacher                               |
| **Zero‑friction**   | Lazy‑imports keep cold‑start fast; `python -m market_toolkit.demo` runs a 20‑second smoke‑test            |

---

## 🚀 Quick start

```bash
pip install -U "pandas numpy ccxt yfinance pandas_ta pantulipy pricelevels pytrends"
```

```python
from market_toolkit import (
    load_crypto_candles, load_stock_candles,
    add_ta, find_double_tops_bottoms, cluster_support_resistance
)

btc = load_crypto_candles('binance', 'BTC/USDT', '1h', 720)
features = add_ta(btc)
print(features.tail())
print(find_double_tops_bottoms(btc))
print(cluster_support_resistance(btc))
```

---

## 🖼️ Next‑JS Dashboard (live demo)

| 👉 **Live demo:** | [https://market-toolkit-demo.vercel.app](https://market-toolkit-demo.vercel.app) |
| ----------------- | -------------------------------------------------------------------------------- |

A slick interview‑ready front‑end built with **React 18 / Next 15 / Tailwind / Recharts**.  It streams candles from a tiny FastAPI shim and overlays detected double‑tops/bottoms.

\### Run locally

```bash
# 1. Start the Python data API
python -m market_toolkit.demo_api  #  → http://localhost:8000/ohlcv

# 2. Next dashboard (in another terminal)
cd examples/next-dashboard
pnpm install
pnpm dev          #  → http://localhost:3000
```

*(Dashboard source lives in `examples/next-dashboard`; keeping it out of the main package avoids bloating imports.)*

---

## 🗄️ File‑tree (v0)

```
market-toolkit/
├─ market_toolkit.py          # ← core library
├─ pyproject.toml             # build metadata (optional)
├─ README.md                  # this file
├─ tests/
│  └─ test_smoke.py           # CI smoke‑test
└─ examples/
   └─ next-dashboard/         # glossy web demo
```

---

## 🤝 Contributing

1. Fork & clone
2. `ruff check . && pytest` must pass
3. Submit PR with clear description / screenshots (for UI bits)

---

## 📜 License

MIT — see `LICENSE` file.
