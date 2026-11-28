<p align="center">
  <a href="README.md"><img src="https://img.shields.io/badge/🌐_Language-English_(Active)-10b981?style=for-the-badge" alt="English"/></a>
  <a href="README.tr.md"><img src="https://img.shields.io/badge/🇹🇷_Dil-T%C3%BCrk%C3%A7e_(Tam_Sayfa)-38bdf8?style=for-the-badge" alt="Türkçe"/></a>
</p>

> ## ⚡ 1-Sentence Install & Quickstart (Antigravity & Claude Code)
> Paste this link into **Antigravity** or **Claude Code** and say:  
> **`"Install this as a plugin on my system: https://github.com/sniplayergamer-hash/token-economy"`**
>
> **3 Steps to Ready:**
> 1. **Install:** Your AI assistant downloads the Ed25519-signed `User Edition` release (`v0.4.5`) and registers the plugin, `PreToolUse` hook, and 12-tool MCP server automatically.
> 2. **Verify:** Ask **"Is Token Economy ready?"** — the AI runs `te_doctor` to verify RTK 1.2.1 filters, the destructive-command safety gate, and Antigravity MCP/hook/skill contracts.
> 3. **Open Cockpit:** Click the **Token Economy** right-pane panel link in chat (or run `py cli.py ui`) to view live verified token savings by project/area, RTK analytics, and optional Mobile Control.
>
> <details>
> <summary><b>🤖 AI Agent Auto-Install Protocol (For Antigravity, Cline &amp; Claude Code)</b></summary>
>
> 1. Download the latest `token-economy-user-*.zip` and `.zip.sig` from GitHub Releases (`sniplayergamer-hash/token-economy`), verify the Ed25519 signature (`maintainer.pub`), and extract to a clean tools directory (e.g. `~/.token-economy/app`).
> 2. **Antigravity:** Run `py plugins/antigravity/install.py` (registers `~/.gemini/config/plugins/token-economy`, 12-tool MCP server, `PreToolUse` hook, 5 bundled skills, and right-pane Sidecar). Surface `[Token Economy](sidecar://token-economy/token_economy_panel/)`.
> 3. **Cline (VS Code / Antigravity IDE):** Run `py plugins/cline/install.py`.
> 4. **Other MCP Clients (Cursor, Windsurf, OpenCode, Claude Desktop):** Run `py plugins/install_all.py --target <client>` (use `--list` to see all targets).
> 5. **Verify:** Run `te_doctor` / `py cli.py doctor` and confirm `antigravity_contract`, `safety_gate`, and `rtk_hook_and_filters` pass.
>
> </details>

<p align="center">
  <img src="https://img.shields.io/badge/Core-12_Deterministic_MCP_Tools-10b981?style=for-the-badge" alt="12 Deterministic MCP Tools"/>
  <img src="https://img.shields.io/badge/Hallucination-0%25_(0--LLM_Core)-38bdf8?style=for-the-badge" alt="Zero Hallucination"/>
  <img src="https://img.shields.io/badge/RTK-1.2.1_CLI_Compression-a855f7?style=for-the-badge" alt="RTK 1.2.1"/>
  <img src="https://img.shields.io/badge/Security-PreToolUse_Gate_%2B_Ed25519-f59e0b?style=for-the-badge" alt="Security"/>
</p>

---

> **Token Economy (`v0.4.5`)** is a **feature-frozen, 0-LLM deterministic MCP server, `PreToolUse` safety/compression hook, and Antigravity right-pane Sidecar cockpit** designed to cut cloud coding token waste with **zero hallucinations and zero VRAM overhead**.

---

## 🎯 Feature-Frozen 12-Tool Deterministic Core

Instead of delegating fragile code edits to small local LLMs, `v0.4.5` focuses exclusively on **12 rock-solid, 100% deterministic tools** (0 LLM, 0 VRAM, 0 `PatchError` loops):

| Category | MCP Tools | What It Does |
| :--- | :--- | :--- |
| **Code Discovery & Impact** | `repo_map`, `local_inspect`, `blast_radius`, `audit_startup` | Fair round-robin symbol map (skips lockfiles like `package-lock.json`/`Cargo.lock` and browser profiles/caches, indexes nested factory functions); AST + verbatim line slicer for large files/JSON/datasets; multi-language impact analysis (including HTML `<script>`); startup rule/context bloat auditor. |
| **CLI Compression & Recall** | `run_slim`, `expand_ref`, `rtk_analytics`, `rtk_manage` | Transparent `PreToolUse` **RTK 1.2.1** command compression (`te-rtk-rewrite`), lossless `@ref` & SQLite recall (`expand_ref`), and live savings analytics (`gain`, `discover`, `hook-audit`, `verify`, `pipe`). |
| **Diagnostics & Context** | `te_status`, `te_doctor`, `hot_state`, `project_mode` | Hardware/RTK/safety-gate/Antigravity MCP & hook contract verification (`te_doctor`), `active_models` visibility reflecting the configured installed default model (`te_status`), 12-line session handoff (`hot_state`), and `general` / `unity` / `blender` project detection. |

---

## 🛡️ Built-In `PreToolUse` Destructive-Command Safety Gate

Running in **0 ms** inside `te_rtk_hook.py` before every `run_command` call (with zero extra processes):
- Hard-blocks catastrophic commands (`rm -rf /`, `mkfs.*`, raw `dd` disk overwrite, `format <Drive>:`, `Format-Volume`, `Remove-Item <Drive>:\ -Recurse -Force`, `rmdir /s /q <Drive>:\`) using Antigravity's native `{"decision": "deny", "reason": "..."}` contract.
- Preserves normal workspace cleanup (`rm -rf dist`, `Remove-Item .\build -Recurse -Force`) and transparent RTK compression.

---

## 📊 Clickable Per-Project Token Savings Cockpit

Open the right-pane Sidecar (`[Token Economy](sidecar://token-economy/token_economy_panel/)`) or run `py cli.py ui`:
- **Clickable Token Savings Card:** Click the verified saved-tokens card to open the **Per-Project & Per-Area Breakdown** modal (`AST/Inspect`, `Slim`, `Dedup`, `RTK CLI`) with recent file/command savings records.
- **One-Click Clear:** Reset telemetry history anytime via the **Clear** button (`POST /api/telemetry/clear`).
- **Auto-Recovery Sidecar:** Automatically refreshes stale daemon tokens on `401` after daemon restarts.

---

## 🧰 5 Bundled Developer Skills

Installed automatically with the Antigravity plugin:
- **`rtk`** — Full RTK 1.2.1 CLI compression, lossless recall, and custom `.rtk/filters.toml` reference.
- **`memory-bank`** — Compact cross-session `memory-bank/` context management.
- **`powershell-windows`** — Windows PowerShell 5.1 / 7+ syntax, UTF-8, `-Depth 10` JSON, and `$LASTEXITCODE` patterns.
- **`rust-pro`** — Modern Rust (2024 edition), ownership/lifetimes, Tokio/axum, `thiserror`/`anyhow`, and Clippy workflows.
- **`api-patterns`** — REST / GraphQL / tRPC contract design, OWASP API Top 10, and bundled `api_validator.py`.

---

## 📱 Optional Mobile Control & Relay WoL

`User Edition` ships with pre-built, Ed25519-signed APKs inside `apk_dist/` (`TokenEconomy-Mobile.apk` and `TokenEconomy-Relay.apk`):
- Protected by a **4-digit anti-theft PIN** set inside your own cockpit.
- Dynamic per-user pairing (`/api/remote/export_apks`) binds the APK strictly to **your own PC's LAN IP, MAC address, port, and session token**.

---

## ⚖️ Copyright & Proprietary License (`All Rights Reserved`)

**Copyright © 2026 Mehmet (`sniplayergamer-hash`). All Rights Reserved.**  
This software is **not** open-source (not MIT/GPL). Users are granted a limited license solely to run the official signed `User Edition`. **Unauthorized copying, forking, redistribution, derivative/competing projects, reverse engineering, or feeding any part of this codebase/architecture into AI/LLM systems for cloning or training is strictly prohibited.** See [LICENSE](LICENSE) for full legal terms.
