<p align="center">
  <a href="README.md"><img src="https://img.shields.io/badge/🌐_Language-English_(Active)-10b981?style=for-the-badge" alt="English"/></a>
  <a href="README.tr.md"><img src="https://img.shields.io/badge/🇹🇷_Dil-T%C3%BCrk%C3%A7e_(Resimli_Tam_Sayfa)-38bdf8?style=for-the-badge" alt="Türkçe"/></a>
</p>

<p align="center">
  <img src="assets/en/hero-banner.svg" alt="Token Economy Banner" width="100%"/>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Quota_Savings-70%25--100%25-10b981?style=for-the-badge" alt="Quota Savings"/>
  <img src="https://img.shields.io/badge/Local_Engine-Ollama_4B%2F7B%2F9B-38bdf8?style=for-the-badge" alt="Ollama"/>
  <img src="https://img.shields.io/badge/Surfaces-Antigravity_Sidecar_%2B_MCP_%2B_CLI-a855f7?style=for-the-badge" alt="Surfaces"/>
  <img src="https://img.shields.io/badge/Security-Ed25519_Signed_%26_Protected-f59e0b?style=for-the-badge" alt="Security"/>
</p>

<details>
<summary><b>🇹🇷 TÜRKÇE KULLANICILAR İÇİN: Resimli &amp; Tasarımlı Orijinal Türkçe Vitrini Burada Aç (veya üstteki 🇹🇷 Türkçe butonuna tıklayın)</b></summary>
<br/>

> Tarayıcı otomatik çevirisi SVG grafiklerin içindeki teknik yazıları bozduğu için **tüm diyagramlar, grafikler ve açıklamalar doğrudan Türkçe olarak da hazırlanmıştır.** Tam ekran Türkçe sayfa için 👉 **[README.tr.md](README.tr.md)**

<p align="center">
  <img src="assets/tr/hero-banner.svg" alt="Token Economy Türkçe Banner" width="100%"/>
</p>
<p align="center">
  <img src="assets/tr/architecture.svg" alt="Token Economy Türkçe Mimari" width="100%"/>
</p>
<p align="center">
  <img src="assets/tr/benchmark-rtx4060ti.svg" alt="Token Economy Türkçe Benchmark" width="100%"/>
</p>
<p align="center">
  <img src="assets/tr/cockpit-preview.svg" alt="Token Economy Türkçe Kokpit" width="100%"/>
</p>

</details>

---

> **Token Economy** is a deterministic local coding harness, MCP server, and Antigravity right-pane Sidecar cockpit — **also usable from Claude Code through standard MCP** — that **slashes cloud coding agent quotas by 70%–95%**, driving local 4B–9B Ollama models (`qwen3.5:4b`, `qwen2.5-coder:7b`, `qwen3.5:9b`) on an 8 GB VRAM GPU with **zero tool-calling hallucinations**.

---

## 🎯 Why Token Economy? (The Real Bottleneck)

Cloud coding quotas aren't burned by high-level architecture—they are burned by **reading 15 files, writing boilerplate, running tests, and fixing minor syntax/import errors across 10+ turns.**  
Conversely, handing 15 raw tools to a 4B–9B local model and asking it to *"explore the repo and build the feature"* leads to malformed JSON tool calls, context overflow, and infinite loops.

**Token Economy solves both with the "Athlete Brain + Deterministic Engine + Apprentice Hand" architecture:**

<p align="center">
  <img src="assets/en/architecture.svg" alt="Token Economy Architecture" width="100%"/>
</p>

1. **Athlete Brain (Antigravity / Cloud Architect):** Scans the symbol map (`repo_map`) in a single turn, slices the work into atomic parts (`Part 1..N`), and dispatches the batch in one MCP call.
2. **Deterministic Python Muscle (0% Tool Hallucination):** File slicing (`read_range`), whitespace-tolerant patching (`fuzzy_patch`), automatic `checkpoint/rollback`, RTK-style log distillation, and non-AI verification (`py_compile`, `node --check`, `pytest`) are executed deterministically by Python—**never left to fragile local tool-calling loops.**
3. **Apprentice Hand (Local Ollama — 100% GPU):** Receives a clean 40-line slice and outputs pure code/diff. On test failure, the engine feeds back only the distilled 15-line error for up to **2× local self-fix retries (0 cloud tokens).**

---

## 📊 Verified Hardware & Quota Benchmarks (RTX 4060 Ti — 8 GB VRAM)

Real empirical measurements on **NVIDIA GeForce RTX 4060 Ti (8 GB VRAM) + 16 GB RAM + Ollama 0.40.16 (`Flash Attention + q8_0 KV Cache`)**:

<p align="center">
  <img src="assets/en/benchmark-rtx4060ti.svg" alt="RTX 4060 Ti Benchmark" width="100%"/>
</p>

| Local Model | Verified 100% GPU `num_ctx` | VRAM Footprint | Generation Speed | Assigned Role |
|---|---:|---:|---:|---|
| **`qwen3.5:4b`** | `16384` | 3.44 GB (100% GPU) | **71.0 tok/s** | `local_inspect` (0-quota file/log summarization), Dream Pass, fast edits |
| **`qwen2.5-coder:7b`** | `16384` | 5.03 GB (100% GPU) | **52.5 tok/s** | Wide-context code generation & surgical `SEARCH/REPLACE` patching |
| **`qwen3.5:latest` (9B)** | `8192` | 5.62 GB (100% GPU) | **44.0 tok/s** | Hard logic & bug fixing (`think: true/false` toggle supported) |

> **Auto-Calibration (`probe_models`):** Automatically detects the highest 100% GPU-resident context ceiling on any 8 GB, 16 GB, 24 GB, or Apple Silicon machine to prevent slow CPU/RAM spillovers.

---

## 🖥️ Antigravity Right-Pane Cockpit & 3 Operating Modes

<p align="center">
  <img src="assets/en/cockpit-preview.svg" alt="Right-Pane Cockpit Preview" width="100%"/>
</p>

### 1. Right-Pane Direct Mode (0% Cloud Quota)
Run everyday coding, refactoring, unit tests, and bug fixes directly from the right-pane Sidecar without touching the main cloud chat. **Cloud quota used: 0.** If a step gets stuck, click **`⚡ ASK ARCHITECT`** to escalate only that slice.

### 2. Architect–Apprentice Hybrid Mode (MCP — 70%–91% Quota Saved)
- **Read Offload (`local_inspect`):** Instead of burning thousands of cloud tokens reading a 600-line file, Antigravity delegates reading to `qwen3.5:4b` (71 tok/s) and receives a structured 12-line digest.
- **Write & Test Offload (`run_parts`):** Antigravity dispatches a 4-part batch in one MCP call; the local daemon runs all patching + `pytest` + local self-fix loops and returns a 15-line summary.

### 3. Terminal CLI (`cli.py`)
```powershell
py cli.py status                                   # Live VRAM, active model, tok/s & saved cloud tokens
py cli.py inspect src/auth.py --query "JWT flow"   # 0-cloud-token file analysis at 71 tok/s
py cli.py run --file src/auth.py --spec "Add leeway_sec to refresh_token" --verify "py -m pytest"
py cli.py bench                                    # Race 4b vs 7b vs 9b across 6 deterministic coding tasks
py cli.py rollback                                 # Instant 1-command undo to pre-edit checkpoint
```

---

## 🛡️ 6-Layer Context Shield & Zero-Trust Self-Evolution

1. **Pinned 100% GPU `num_ctx`** (Eliminates model cold-reloads between turns)
2. **`keep_alive` Lock** (Overrides host `OLLAMA_KEEP_ALIVE=1` to keep weights hot in VRAM during active jobs)
3. **Byte-Identical KV Prefix Cache** (Speeds up multi-turn prompt prefill by 3–5×)
4. **AST Symbol & Line Slicing (`repo_map` + `read_range`)**
5. **RTK Noise Distiller & Observation Masking**
6. **`70%` Rolling Compaction + 12-Line `.token-economy/hot.md`**

### 🧬 `Saver` ↔ `Lab` Self-Evolution & Ed25519 Signed Ecosystem
- **🟢 `Saver Mode` (Default):** 0 extra cloud tokens. Runs silent local telemetry (`telemetry.jsonl`), 12-line `hot.md` handoff, and local `Dream Pass` (`lessons.json`).
- **🟣 `Lab (Self-Evolve) Mode`:** Auto-tunes model parameters, profiles, and filters for your hardware and language stack behind a strict benchmark + `auto-rollback` gate.
- **🔒 Signed Community Extensions:** You can submit your own code-free `extensions/` rules (profiles, log filters, language rules) from the official client. Selected proposals are verified and shipped in the official signed release.

---

## ⚖️ Copyright & Proprietary License (`All Rights Reserved`)

**Copyright © 2026 Mehmet (`sniplayergamer-hash`). All Rights Reserved.**  
This software is **not** open-source (not MIT/GPL). Users are granted a limited license solely to run the official signed `User Edition` and submit declarative extension proposals. **Unauthorized copying, forking, redistribution, derivative/competing projects, reverse engineering, or feeding any part of this codebase/architecture into AI/LLM systems for cloning or training is strictly prohibited.** See [LICENSE](LICENSE) for full legal terms.
