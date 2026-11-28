<p align="center">
  <a href="README.md"><img src="https://img.shields.io/badge/🌐_Language-English-334155?style=for-the-badge" alt="English"/></a>
  <a href="README.tr.md"><img src="https://img.shields.io/badge/🇹🇷_Dil-T%C3%BCrk%C3%A7e_(Aktif)-10b981?style=for-the-badge" alt="Türkçe"/></a>
</p>

> ## ⚡ Tek Cümleyle Kurulum & Hızlı Başlangıç (Antigravity & Claude Code)
> Bu bağlantıyı **Antigravity** veya **Claude Code** sohbetine yapıştırıp şunu yazmanız yeterlidir:  
> **`"Bunu sistemime eklenti olarak kur: https://github.com/sniplayergamer-hash/token-economy"`**
>
> **3 Adımda Hazır:**
> 1. **Kurulum:** Yapay zekâ ajanı Ed25519 imzalı `User Edition` (`v0.4.5`) paketini indirip eklentiyi, `PreToolUse` kancasını ve 12 araçlık MCP sunucusunu otomatik kurar.
> 2. **Doğrulama:** **"Eklenti kullanıma hazır mı?"** diye sorun — ajan `te_doctor` çalıştırarak RTK 1.2.1 filtrelerini, yıkıcı komut güvenlik kilidini ve Antigravity MCP/hook/beceri kontratlarını doğrular.
> 3. **Kokpit:** Sohbetteki **Token Economy** sağ panel bağlantısına tıklayın (veya `py cli.py ui` çalıştırın); proje/alan bazlı gerçek token tasarrufunu, RTK istatistiklerini ve isteğe bağlı Mobil Kontrolü canlı izleyin.
>
> <details>
> <summary><b>🤖 Yapay Zekâ Ajanı İçin Otomatik Kurulum Protokolü (Antigravity, Cline &amp; Claude Code)</b></summary>
>
> 1. GitHub Releases (`sniplayergamer-hash/token-economy`) üzerinden son `token-economy-user-*.zip` + `.zip.sig` paketini indirin, Ed25519 imzasını (`maintainer.pub`) doğrulayıp yerel bir klasöre (`~/.token-economy/app`) açın.
> 2. **Antigravity:** `py plugins/antigravity/install.py` komutunu çalıştırın (12 araçlık MCP sunucusu, `PreToolUse` kancası, 5 beceri ve sağ panel Sidecar otomatik kurulur); sohbette `[Token Economy](sidecar://token-economy/token_economy_panel/)` bağlantısını sunun.
> 3. **Cline (VS Code / Antigravity IDE):** `py plugins/cline/install.py` komutunu çalıştırın.
> 4. **Diğer MCP İstemcileri (Cursor, Windsurf, OpenCode, Claude Desktop):** `py plugins/install_all.py --target <istemci>` komutunu çalıştırın (`--list` ile tüm hedefleri görün).
> 5. **Doğrulama:** `te_doctor` / `py cli.py doctor` çalıştırıp `antigravity_contract`, `safety_gate` ve `rtk_hook_and_filters` sonuçlarını raporlayın.
>
> </details>

<p align="center">
  <img src="https://img.shields.io/badge/%C3%87ekirdek-12_Deterministik_MCP_Arac%C4%B1-10b981?style=for-the-badge" alt="12 Deterministik MCP Aracı"/>
  <img src="https://img.shields.io/badge/Hal%C3%BCsinasyon-%250_(0--LLM_%C3%87ekirdek)-38bdf8?style=for-the-badge" alt="Sıfır Halüsinasyon"/>
  <img src="https://img.shields.io/badge/RTK-1.2.1_CLI_S%C4%B1k%C4%B1%C5%9Ft%C4%B1rma-a855f7?style=for-the-badge" alt="RTK 1.2.1"/>
  <img src="https://img.shields.io/badge/G%C3%BCvenlik-PreToolUse_Kilidi_%2B_Ed25519-f59e0b?style=for-the-badge" alt="Güvenlik"/>
</p>

---

> **Token Economy (`v0.4.5`)**, bulut kodlama ajanlarının token israfını **sıfır halüsinasyon ve sıfır VRAM yüküyle** azaltan, özellikleri dondurulmuş (feature-frozen) **12 araçlık deterministik MCP sunucusu, `PreToolUse` güvenlik/sıkıştırma kancası ve Antigravity sağ panel kokpitidir.**

---

## 🎯 Özellikleri Dondurulmuş 12 Araçlık Deterministik Çekirdek

`v0.4.5`, küçük yerel LLM'lerle kırılgan kod düzenleme döngülerine girmek yerine yalnızca **%100 deterministik 12 çekirdek araca** odaklanır (0 LLM, 0 VRAM, 0 `PatchError` döngüsü):

| Kategori | MCP Araçları | Ne İşe Yarar? |
| :--- | :--- | :--- |
| **Kod Keşfi & Etki Analizi** | `repo_map`, `local_inspect`, `blast_radius`, `audit_startup` | Kilit dosyalarını (`package-lock.json`, `Cargo.lock` vb.) ve tarayıcı profil/önbelleklerini atlayan, üst dizinleri dengeli (round-robin) haritalayan ve iç içe fabrika fonksiyonlarını indeksleyen sembol haritası; büyük dosyalar/JSON/veri setleri için deterministik AST + birebir satır kesiti; Python/JS/TS/HTML `<script>`/C#/Rust/Go etki analizi; başlangıç kural/bağlam şişmesi denetimi. |
| **CLI Sıkıştırma & Geri Çağırma** | `run_slim`, `expand_ref`, `rtk_analytics`, `rtk_manage` | Şeffaf `PreToolUse` **RTK 1.2.1** komut sıkıştırma kancası (`te-rtk-rewrite`), kayıpsız `@ref` ve SQLite geri açma (`expand_ref`) ve canlı tasarruf analitiği (`gain`, `discover`, `hook-audit`, `verify`, `pipe`). |
| **Tanı & Oturum Bağlamı** | `te_status`, `te_doctor`, `hot_state`, `project_mode` | Donanım, RTK filtreleri, güvenlik kilidi ve Antigravity MCP/hook/beceri kontrat doğrulaması (`te_doctor`), kurulu varsayılan modeli yansıtan `active_models` görünürlüğü (`te_status`), 12 satırlık oturum belleği (`hot_state`) ve `general` / `unity` / `blender` proje tespiti. |

---

## 🛡️ Dahili `PreToolUse` Yıkıcı Komut Güvenlik Kilidi

Her `run_command` çağrısından önce ek süreç başlatmadan **0 ms** içinde (`te_rtk_hook.py`) çalışır:
- Kök dizin silme (`rm -rf /`), dosya sistemi formatlama (`mkfs.*`), ham disk ezme (`dd`), Windows sürücü formatlama (`format C:`, `Format-Volume`) ve sürücü kökü silme (`Remove-Item C:\ -Recurse -Force`, `rmdir /s /q C:\`) komutlarını Antigravity'nin yerel `{"decision": "deny", "reason": "..."}` kontratıyla anında bloklar.
- Normal proje temizliğine (`rm -rf dist`, `Remove-Item .\build -Recurse -Force`) ve şeffaf RTK sıkıştırmasına dokunmaz.

---

## 📊 Tıklanabilir Proje Bazlı Token Tasarruf Kokpiti

Sağ panelden (`[Token Economy](sidecar://token-economy/token_economy_panel/)`) veya `py cli.py ui` ile açılır:
- **Tıklanabilir Token Kutusu:** Tasarruf kutusuna (`~karakter / 4` yerel ölçüm tahmini, fatura verisi değildir) tıkladığınızda **Proje & Alan Bazlı Kırılım** penceresi açılır; hangi projede hangi alandan (`AST/Inspect`, `Slim`, `Dedup`, `RTK CLI`) ne kadar tasarruf edildiğini ve son kayıtları canlı gösterir.
- **RTK Notu:** CLI komut sıkıştırması için isteğe bağlı harici `rtk` aracı (`https://github.com/rtk-ai/rtk`) gerekir. `rtk` kurulu değilse `PreToolUse` kancası yine de yıkıcı komut güvenlik kilidini sorunsuz çalıştırır.
- **Varsayılan Güvenlik (`v0.4.5`):** Daemon varsayılan olarak yalnızca `127.0.0.1` (yerel makine) üzerinde dinler; `GET /` localhost dışına asla oturum tokenı gömmez; mobil kontrol PIN ayarlanmadan açılmaz (fail-closed); `rtk_binary_path` ağ paylaşımı yollarını reddeder; güncelleme doğrulaması sabit `maintainer.pub` Ed25519 anahtarıyla yapılır.
- **Tek Tıkla Temizleme:** Detay penceresindeki **🧹 Temizle** düğmesiyle (`POST /api/telemetry/clear`) tasarruf geçmişini istediğiniz an sıfırlayabilirsiniz.

---

## 🧰 5 Dahili Geliştirici Becerisi (Skills)

Antigravity eklentisiyle birlikte otomatik kurulur:
- **`rtk`** — RTK 1.2.1 CLI sıkıştırma, kayıpsız geri çağırma ve `.rtk/filters.toml` rehberi.
- **`memory-bank`** — Oturumlar arası kompakt `memory-bank/` proje bağlamı yönetimi.
- **`powershell-windows`** — Windows PowerShell 5.1 / 7+ sözdizimi, UTF-8, `-Depth 10` JSON ve `$LASTEXITCODE` kalıpları.
- **`rust-pro`** — Modern Rust (2024), ownership/lifetime, Tokio/axum, `thiserror`/`anyhow` ve Clippy iş akışları.
- **`api-patterns`** — REST / GraphQL / tRPC sözleşme tasarımı, OWASP API Top 10 ve dahili `api_validator.py`.

---

## 📱 İsteğe Bağlı Mobil Kontrol & Röle WoL

`User Edition` paketi içinde hazır ve Ed25519 imzalı APK'lar (`apk_dist/TokenEconomy-Mobile.apk` ve `TokenEconomy-Relay.apk`) yer alır:
- Kokpitten belirlenen **4 haneli çalınma korumalı PIN** ile korunur.
- Dinamik kullanıcı bazlı eşleştirme (`/api/remote/export_apks`) APK'yı yalnızca **kullanıcının kendi bilgisayarının LAN IP, MAC adresi, portu ve oturum tokenına** bağlar.

---

## ⚖️ Lisans (`MIT`)

[MIT Lisansı](LICENSE) altında yayınlanmıştır © 2026 Mehmet (`sniplayergamer-hash`). Bağımsız güvenlik incelemeleri ve yerel özelleştirmeler serbesttir.
