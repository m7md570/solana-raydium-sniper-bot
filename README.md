# 🎯 Solana Fast Token Liquidity & Raydium Sniper Bot

[![Solana Mainnet](https://img.shields.io/badge/Solana-Mainnet--Beta-9945FF?style=flat-square&logo=solana)](https://solana.com)
[![Python 3.10+](https://img.shields.io/badge/Python-3.10%2B-blue?style=flat-square&logo=python)](https://python.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg?style=flat-square)](LICENSE)
[![Latency Benchmark](https://img.shields.io/badge/Execution%20Speed-%3C400ms-brightgreen?style=flat-square)]()
[![Rug Protection](https://img.shields.io/badge/Anti--Rug%20Filters-Enabled-blueviolet?style=flat-square)]()

A high-performance asynchronous Python sniper bot engineered for instantaneous new token liquidity detection and automated trading on Solana (**Raydium CPMM**, **Pump.fun**, and **Jupiter routes**).

---

## 🚀 Key Architectural Features

- **⚡ Sub-400ms Event Sniping:** Asynchronous WebSocket listener monitoring Raydium pool creation program logs (`675kPX9MHTjS2zt1qfr1NYHuzeLXfQM9H24wFSUt1Mp8`).
- **🛡️ Deterministic Anti-Rug Guard:** Real-time pre-trade validation:
  - Verified `mintAuthority == null` (Mint disabled)
  - Verified `freezeAuthority == null` (Freeze disabled)
  - RugCheck API scoring threshold validation
- **💰 Automated Trade Execution & Risk Management:**
  - Configurable Take-Profit (`+25%`) and Stop-Loss (`-10%`) triggers.
  - Dynamic Trailing Stop to ride upside momentum.
  - Auto-closing of associated token accounts (ATA) to reclaim Solana account rent.
- **⚡ Jito Bundle Tip Support:** Direct execution via Jito block builders to mitigate public mempool sandwich and frontrunning attacks.

---

## 🛠️ Quick Start

### 1. Installation
```bash
git clone https://github.com/m7md570/solana-raydium-sniper-bot.git
cd solana-raydium-sniper-bot
pip install -r requirements.txt
```

### 2. Configuration
Copy the configuration example:
```bash
cp config.example.json config.json
```

Edit `config.json` with your custom settings:
```json
{
  "rpc_endpoints": [
    "https://api.mainnet-beta.solana.com",
    "https://solana-rpc.publicnode.com"
  ],
  "trading": {
    "default_buy_amount_sol": 0.1,
    "max_slippage_bps": 100,
    "take_profit_pct": 25.0,
    "stop_loss_pct": 10.0
  },
  "safety_filters": {
    "max_rugcheck_score": 500,
    "require_mint_renounced": true,
    "require_freeze_renounced": true
  }
}
```

### 3. Launching the Sniper
```bash
python sniper.py
```

---

## ☕ Support & Donations

If this sniper bot assists your on-chain trading operations, support future open-source development:

- **Solana Wallet (SOL / USDC / SPL Tokens):**
  ```text
  7kz1mcQcaZhYzFUHBFHH6s5tGrDHc7gNhN5WAUyXyq5r
  ```

---

## 📄 License
This project is released under the [MIT License](LICENSE).
