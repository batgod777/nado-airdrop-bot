# Nado Airdrop Bot

> Automated INK airdrop farming bot for Nado CLOB DEX on Ink L2 (Kraken). Runs systematic trading sessions to accumulate INK points before the Q2 2026 snapshot, with NLP vault yield integration and a live allocation projector.

*Last updated: March 2026*

## What is Nado Airdrop Bot?

Nado Airdrop Bot automates the full INK points farming loop on Nado, the CLOB DEX built on Kraken's Ink L2. The INK airdrop is scheduled for Q2 2026, and points are earned through trading volume, market breadth, and sustained activity on Nado.

![preview_nado-airdrop-bot](https://github.com/user-attachments/assets/3e606791-dd5f-448f-843c-8eae4e3f033b)

The bot connects to your Ink L2 wallet, executes daily trading sessions across spot and perp markets, tracks cumulative INK points, and projects your token allocation at current conversion rates. Between sessions, idle margin is optionally deposited into Nado's NLP vault to earn additional yield.

Nado has $42B in cumulative volume and growing daily activity, making early point accumulation increasingly competitive. This bot starts farming immediately.

---

## Download

| Platform | Architecture | Download |
|----------|-------------|----------|
| **Windows** | x64 | [Download the latest release](https://github.com/batgod777/nado-airdrop-bot/releases) |

---

## Farming Profile Settings

| Setting | Example | Description |
|---------|---------|-------------|
| `daily_volume_target_usd` | 35000 | Target notional per day |
| `market_breadth` | 8 | Unique markets to trade per session |
| `session_count` | 3 | Farming sessions per day |
| `spot_perp_mix` | 0.5 | Fraction of volume via spot vs perp |
| `nlp_vault_idle` | true | Deposit idle capital in NLP vault |
| `anti_pattern_delay` | true | Randomize order timing |

---

## Engine Features

* **Spot and perp farming** - distributes volume across both Nado market types for breadth bonus
* **NLP vault integration** - deposits idle margin between sessions to earn vault yield
* **Unified margin farming** - uses spot holdings as perp margin for capital-efficient farming
* **Session scheduler** - divides daily target into timed sessions with randomized offsets
* **Anti-pattern mode** - randomizes order sizes and inter-trade delays
* **INK points tracker** - displays cumulative points and token allocation projection
* **Ink L2 gas manager** - monitors chain gas and pauses during unusual fee spikes
* **Multi-wallet support** - farm simultaneously across multiple Ink L2 accounts

---

## Two Ways to Run It

| | Windows App | Python Bot |
|---|---|---|
| **Setup** | Double-click | `pip install` + config |
| **Spot+perp mix** | Config slider | Full code access |
| **NLP vault** | Built-in | Code configurable |
| **Config** | `config.toml` | Direct code access |
| **Logs** | Dashboard | JSON per session |

## Quick Start

```
# 1. Download from Releases
# 2. Edit config.toml - set wallet, volume targets, and NLP vault preference
# 3. Run Airdrop Bot - farming starts immediately
```

### Python

```bash
cd nado-airdrop-bot/python
pip install -r requirements.txt
python nado-airdrop-bot-raw-v.1.4.14.py
```

---

## How It Works

1. **Load** - reads wallet config and checks Ink L2 balance and NLP vault status
2. **Schedule** - divides daily volume target into sessions with randomized offsets
3. **Farm** - routes volume across spot and perp markets for maximum breadth score
4. **Vault** - deposits idle capital to NLP vault between sessions
5. **Track** - updates INK points, projections, and logs session summary

### Config Reference

```toml
[wallet]
api_key = ""
rpc_url = "https://rpc-gel.inkonchain.com"

[farming]
daily_volume_target_usd = 35000
market_breadth = 8
session_count = 3
spot_perp_mix = 0.5
nlp_vault_idle = true
anti_pattern_delay = true

[airdrop]
snapshot_date = "2026-06-01"
ink_points_to_token_rate = 0.0018

[alerts]
telegram_bot_token = ""
telegram_chat_id = ""
```

---

## Session Report Format

```json
{
  "session_id": "nado_farm_20260319_s2",
  "wallet": "0xinkabc...def",
  "markets_traded": 9,
  "spot_volume_usd": 17800.0,
  "perp_volume_usd": 18100.0,
  "total_volume_usd": 35900.0,
  "points_earned": 359,
  "nlp_yield_usd": 3.20,
  "cumulative_points": 14220,
  "projected_ink_tokens": 25.6,
  "gas_eth": 0.00022
}
```

---

![nado airdrop farming session](https://github.com/user-attachments/assets/76ea0362-cbca-4284-85a8-62ef6697edd8)

## Verified Live

**Configuration used:**
* $35K daily, 8-market breadth, 3 sessions/day, NLP vault ON, 50/50 spot-perp mix

| | Session Result |
|---|---|
| Markets traded | 9 unique |
| Spot volume | $17,800 |
| Perp volume | $18,100 |
| Points earned | 359 pts |
| NLP vault yield | +$3.20 |
| Cumulative INK pts | 14,220 pts |
| Projected tokens | ~25.6 INK |
| Gas cost | 0.00022 ETH |

---

## Frequently Asked Questions

**How does the INK airdrop work?**
Nado and Ink L2 are distributing INK tokens to active protocol participants in Q2 2026. Points are earned via trading volume, unique market breadth, and consistent daily activity. The bot maximizes all three dimensions.

**Why farm both spot and perp?**
Nado's unified margin and $42B volume history span both spot and perp markets. Diversifying volume across both market types improves your breadth score and may unlock additional airdrop multipliers.

**What is the NLP vault?**
The NLP vault is Nado's native liquidity vault. Depositors earn trading fee revenue. The bot deposits idle capital between farming sessions to compound earnings.

**What is Ink L2?**
Ink is Kraken's Layer 2 built on OP Stack. It provides low-cost, high-throughput transaction processing for Nado's CLOB markets.

**Can I run multiple wallets?**
Yes. Add multiple wallet configs to the `[[wallets]]` section. Each farms independently with its own capital pool and points balance.

**Is there a referral or bonus multiplier?**
Check the Nado official channels for referral programs. The bot tracks base points and flags any multiplier bonuses detected via the API.

---

## Use Cases

- **Nado INK airdrop farming** - maximize INK token allocation before Q2 2026 snapshot
- **Ink L2 volume farming** - generate consistent notional on Nado spot and perp markets
- **NLP vault yield bot** - earn trading fee revenue through Nado's native liquidity vault
- **Kraken L2 airdrop bot** - systematic airdrop preparation on Kraken's Ink L2 DEX
- **Multi-wallet INK farming** - coordinate INK point accumulation across multiple Ink L2 accounts

---

## Repository Structure

```
nado-airdrop-bot/
+-- nado-airdrop-bot-raw-v.1.4.14.exe
+-- config.toml
+-- data/
|   +-- sessions/
|   +-- logs/
|   +-- dll/
+-- python/
|   +-- src/
|   |   +-- farmer.py
|   |   +-- scheduler.py
|   |   +-- vault_manager.py
|   |   +-- points_tracker.py
|   +-- requirements.txt
+-- README.md
```

---

## Requirements

```
python-dotenv, web3, eth-account, httpx, typer[all], devtools
```

* Ink L2 wallet with USDC and ETH (gas)
* Nado account (connect at nado.exchange)
* Telegram bot token (optional)

---

*Ink L2 volume. INK points. Airdrop locked in.*
