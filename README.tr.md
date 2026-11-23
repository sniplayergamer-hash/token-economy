<p align="center">
  <a href="README.md"><img src="https://img.shields.io/badge/🌐_Language-English-334155?style=for-the-badge" alt="English"/></a>
  <a href="README.tr.md"><img src="https://img.shields.io/badge/🇹🇷_Dil-T%C3%BCrk%C3%A7e_(Aktif)-10b981?style=for-the-badge" alt="Türkçe"/></a>
</p>

> ## ⚡ Tek Cümleyle Kurulum & 4 Adımda Hızlı Kullanım (Antigravity & Claude Code)
> Bu GitHub bağlantısını **Antigravity** veya **Claude Code** sohbetine yapıştırıp şunu yazmanız yeterlidir:  
> **`"Bunu sistemime eklenti olarak kur: https://github.com/sniplayergamer-hash/token-economy"`**
>
> **4 Adımda Hazır Hale Getirme:**
> 1. **Kurulum:** Yapay zekâ ajanı Ed25519 imzalı `User Edition` sürümünü otomatik indirip eklenti ve MCP bağlantısını kurar.
> 2. **Donanım Tarama & Doğrulama:** **"Eklenti kullanıma hazır mı?"** diye sorun — ajan `te_doctor` çalıştırıp ekran kartınızın VRAM'ini tarar, taşmayacak güvenli yerel modeli önerir/kurar ve canlı test sonucunu yazar.
> 3. **Sağ Panel Kullanımı:** Sohbette sunulan **Token Economy** sağ panel bağlantısını açın (Claude Code'da `py cli.py ui`); dilinizi, `Saver` (0 ek bulut kotası) / `Lab` modunu ve anında VRAM boşaltan `ON / OFF` anahtarını seçin.
> 4. **(İsteğe bağlı) Mobil Kontrol & Uzaktan PC Aç/Kapat:** Eklenti panelinden **4 haneli çalınma korumalı PIN** belirleyip `TokenEconomy-Mobile.apk`'yı eşleştirin; Wi-Fi dışından PC açmak için sabit `TokenEconomy-Relay.apk`'yı evdeki 2. telefona 1 kez kurun (hem Ev Wi-Fi hem Mobil Veri açık). Eklenti içindeki **`❓`** düğmesinden adım adım rehbere her an ulaşabilirsiniz.
>
> <details>
> <summary><b>🤖 Yapay Zekâ Ajanı İçin Otomatik Kurulum Protokolü (Antigravity &amp; Claude Code)</b></summary>
>
> 1. GitHub Releases (`sniplayergamer-hash/token-economy`) üzerinden son `token-economy-user-*.zip` + `.zip.sig` paketini indirin, Ed25519 imzasını (`maintainer.pub`) doğrulayıp yerel bir klasöre (`~/.token-economy/app`) açın.
> 2. **Antigravity:** `py plugins/antigravity/install.py` komutunu çalıştırın (eklenti, MCP sunucusu ve sağ panel Sidecar otomatik kurulur); sohbette tek tık panel bağlantısı `[Token Economy](sidecar://token-economy/token_economy_panel/)` bağlantısını sunun.
> 3. **Cline (Antigravity IDE / VS Code):** `py plugins/cline/install.py` komutunu çalıştırın (`cline_mcp_settings.json` içine `token-economy` MCP sunucusunu ve `~/Documents/Cline/Rules/token-economy.md` global kuralını otomatik ekler).
> 4. **Diğer MCP İstemcileri (OpenCode, OpenClaw/Claw, Hermes, Cursor, Windsurf, Claude Desktop):** `py plugins/install_all.py --target <istemci>` komutunu çalıştırın (tüm liste için `--list`).
> 5. **Claude Code:** `/plugin marketplace add sniplayergamer-hash/token-economy` -> `/plugin install token-economy@token-economy` ile kurun; kokpiti tarayıcıda açmak için `py cli.py ui` çalıştırın.
> 6. **Otomatik Donanım Tarama & Canlı Test:** Kurulum biter bitmez `te_doctor` (veya `py cli.py doctor`) çalıştırın. Güvenli model kurulu değilse `recommended_pull` modelini `py cli.py pull <model>` ile kurup kalibre edin ve `ready: true` kanıtıyla kullanıcıya bildirin.
>
> </details>

<p align="center">
  <img src="assets/tr/hero-banner.svg" alt="Token Economy Türkçe Banner" width="100%"/>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kota_Tasarrufu-%2570--%25100-10b981?style=for-the-badge" alt="Kota Tasarrufu"/>
  <img src="https://img.shields.io/badge/Yerel_Motor-Ollama_4B%2F7B%2F9B-38bdf8?style=for-the-badge" alt="Ollama"/>
  <img src="https://img.shields.io/badge/Aray%C3%BCz-Antigravity_Sa%C4%9F_Panel_%2B_MCP_%2B_CLI-a855f7?style=for-the-badge" alt="Arayüz"/>
  <img src="https://img.shields.io/badge/G%C3%BCvenlik-Ed25519_%C4%B0mzal%C4%B1_%26_Korumal%C4%B1-f59e0b?style=for-the-badge" alt="Güvenlik"/>
</p>

> **Token Economy**, bulut kodlama ajanlarının pahalı token kotasını **%70 ila %95 oranında düşüren** deterministik kodlama motoru, MCP sunucusu ve **Antigravity** sağ panel kokpitidir; standart MCP sayesinde **Claude Code ile de çalışır**. 8 GB VRAM'li standart bir ekran kartında bile yerel Ollama modellerini (`qwen3.5:4b`, `qwen2.5-coder:7b`, `qwen3.5:9b`) **sıfır araç halüsinasyonuyla** çalıştırır.

---

## 🎯 Neden Token Economy? (Çözdüğü Gerçek Sorun)

Bulut kodlama ajanlarında kotayı bitiren şey "mimari düşünme" değildir; **15 dosya okumak, boilerplate yazmak, test koşmak ve küçük syntax/import hatalarını 10 tur boyunca düzeltmektir.**  
Öte yandan küçük yerel modellere (4B–9B) doğrudan 15 araç verip *"tüm projeyi gez ve kodla"* dediğinizde JSON şeması bozulur, context taşar ve döngüye girer.

**Token Economy bu ikilemi "Atlet Beyin + Deterministik Motor + Çırak El" mimarisiyle çözer:**

<p align="center">
  <img src="assets/tr/architecture.svg" alt="Token Economy Mimarisi" width="100%"/>
</p>

1. **Atlet Beyin (Antigravity / Bulut Mimar):** Projeyi sembol haritasıyla (`repo_map`) tek turda tarar, işi küçük atomik parçalara (`Part 1..N`) böler ve tek bir MCP çağrısıyla yerel motora devreder.
2. **Deterministik Python Kas Sistemi (0 Araç Halüsinasyonu):** Dosya okuma (`read_range`), toleranslı yama (`fuzzy_patch`), otomatik `checkpoint/rollback`, RTK-tarzı log gürültü damıtma ve AI'sız doğrulama (`py_compile`, `node --check`, `pytest`) işlerini **Ollama'ya bırakmaz, doğrudan Python yürütür.**
3. **Çırak El (Yerel Ollama — %100 GPU):** Karmaşık tool-calling kararı vermez; önüne konan 40 satırlık kesite göre sadece temiz kod/yama üretir. Test patlarsa bulut ajanını uyandırmadan **yerelde 2 kez kendi kendini tamir eder (0 bulut kotası).**

---

## 📊 Gerçek Donanım & Kota Ölçümleri (RTX 4060 Ti — 8 GB VRAM)

<p align="center">
  <img src="assets/tr/benchmark-rtx4060ti.svg" alt="RTX 4060 Ti Benchmark" width="100%"/>
</p>

| Yerel Model | Güvenli %100 GPU `num_ctx` | VRAM Kullanımı | Üretim Hızı | Görevdeki Rolü |
|---|---:|---:|---:|---|
| **`qwen3.5:4b`** | `16384` | 3.44 GB (%100 GPU) | **71.0 tok/s** | `local_inspect` (0-kota dosya/log özetleme), Dream Pass, hızlı yama |
| **`qwen2.5-coder:7b`** | `16384` | 5.03 GB (%100 GPU) | **52.5 tok/s** | Geniş bağlamlı saf kod üretimi ve cerrahi `SEARCH/REPLACE` yaması |
| **`qwen3.5:latest` (9B)** | `8192` | 5.62 GB (%100 GPU) | **44.0 tok/s** | Karmaşık mantık ve zor hata ayıklama (`think: true/false` destekli) |

### ✅ Ölçülen kodlama doğruluğu (Token Economy motoru, 6 deterministik görev, gerçek kod doğrulamalı)

| Model | Geçen | Oto-tamir turu | Ort. hız | Toplam süre |
|---|---:|---:|---:|---:|
| `qwen3.5:4b` | **6/6** | 1 | 67.8 tok/s | 15.5 s |
| `qwen3.5:latest` (9B) | **6/6** | 1 | 41.3 tok/s | 21.3 s |
| `qwen2.5-coder:7b` | 5/6 | 2 | 50.3 tok/s | 15.3 s |

> Not: 6 küçük görevlik ilk set; varsayılan model bu sonuca göre `qwen3.5:4b`. Yukarıdaki "kota" grafiği **tahmini bir senaryodur**, henüz gerçek bulut ölçümü değildir; görseller tasarım önizlemesidir.

---

## 🖥️ Antigravity Sağ Panel Kokpiti & 3 Çalışma Modu

<p align="center">
  <img src="assets/tr/cockpit-preview.svg" alt="Sağ Panel Kokpit Önizlemesi" width="100%"/>
</p>

1. **Sağ Panel Doğrudan Mod (%0 Bulut Kotası):** Rutin kodlama, refactor, birim test ve hata düzeltmelerini Antigravity ana sohbetine hiç yazmadan doğrudan sağ panelden yerel motora yaptırın. Takıldığı noktada tek tuşla (**`⚡ Üst Akla Danış`**) yalnız o parçayı Antigravity'ye sorun.
2. **Usta–Çırak Hibrit Modu (MCP — %70–%91 Kota Tasarrufu):** `local_inspect` ile büyük dosyaları 0 bulut tokenıyla `qwen3.5:4b` özetler; `run_parts` ile çoklu-parça kodlama ve test döngüsü yerelde tamamlanır.
3. **Terminal CLI (`cli.py`):**
   ```powershell
   py cli.py status                                  # Canlı VRAM, aktif model, tok/s ve kurtarılan kota
   py cli.py inspect src/auth.py --query "JWT akışı" # 0 bulut tokenı ile hızlı dosya analizi (71 tok/s)
   py cli.py run --file src/auth.py --spec "refresh_token içine leeway parametresi ekle" --verify "py -m pytest"
   py cli.py bench                                   # 4b vs 7b vs 9b modellerini 6 gerçek görevde yarıştır
   py cli.py rollback                                # Son yamayı tek komutla geri al
   ```

---

## 🛡️ Context Sınırına Karşı 6'lı Zırh & Zero-Trust İmzalı Öz-Evrim

- **6'lı Context Zırhı:** Sabit %100 GPU `num_ctx`, `keep_alive` kilidi, byte-sabit KV Prefix Cache, AST sembol kesiti (`repo_map`), RTK log damıtıcı + observation masking, `%70` rolling compaction ve 12 satırlık `.token-economy/hot.md`.
- **`Saver` ↔ `Lab` Modu:** `Saver` modunda %0 ek bulut maliyeti; `Lab` modunda kendi GPU ve proje dilinize göre benchmark kapılı (`auto-rollback` korumalı) öz-evrim.
- **İmzalı Topluluk Önerileri:** Kendi geliştirdiğiniz kodsuz `extensions/` kurallarını (profil, log filtresi, dil kuralı) resmî istemciden gönderebilirsiniz. Seçilen öneriler doğrulanıp resmî imzalı sürüme eklenir.

---

## ⚖️ Telif Hakkı ve Lisans (`All Rights Reserved`)

**Copyright © 2026 Mehmet (`sniplayergamer-hash`). Tüm Hakları Saklıdır.**  
Bu yazılım açık kaynaklı (MIT/GPL) **değildir**. Telif sahibinin yazılı izni olmadan **kopyalanması, çatallanması (fork), türev/benzer proje yapılması, tersine mühendislik uygulanması veya kodlarının/mimarisinin yapay zekâ modellerine okutularak klonlatılması** kesinlikle yasaktır. Ayrıntılar için [LICENSE](LICENSE) dosyasına bakınız.

<!-- TE_HW_GUIDE_START -->
### Donanım VRAM Rehberi, ON/OFF Güç Anahtarı, RTK 1.2.1 Köprüsü, Unity KitWright MCP & Mobil APK (`v0.4.3`)
- **Otomatik VRAM Kilidi:** Canlı GPU bütçesinin %88'ini aşan modeller ekran kartını kilitlemesin diye kilitlenir (`6GB: 4b` · `8GB: 4b/7b/9b` · `16GB: 14b` · `24-32GB+: 32b`).
- **ON/OFF VRAM Boşaltma:** **KAPALI** yapıldığında tüm modeller `ollama stop` + `keep_alive: 0` ile boşaltılıp GPU anında serbest kalır.
- **RTK 1.2.1 Tam Köprü & Memory Bank (`v0.4.3`):** Şeffaf `PreToolUse` CLI sıkıştırma kancası (`te-rtk-rewrite`), kayıpsız SQLite/`@ref` geri çağırma (`expand_ref`), `rtk_analytics` (`gain`, `discover`, `hook-audit`, `learn`) ve `rtk_manage` (`verify`, `trust`, `pipe`, `llm-proxy`) MCP araçları, sağ panel canlı RTK kokpiti ve oturumlar arası `memory-bank/` becerisi.
- **Unity & Blender Modu:** 3D sahne, geometri, shader ve KitWright MCP `execute_code` adımlarını bulut mimarda tutar; C# `repo_map`, `local_inspect` ve kablolamayı yerel Ollama'ya devreder.
- **Mobil Kontrol APK & Sabit 2. Cihaz Röle (`v0.4.3`):** **Antigravity**, **Masaüstü** ve **Unity/Blender** ekranlarını eklentiden belirlenen **4 haneli çalınma korumalı PIN** ile mobilden canlı yönetin ve LAN üzerinden tek tıkla OTA APK güncelleyin. Wi-Fi dışından PC açmak için sabit **TokenEconomy-Relay.apk**'yı evde duran 2. telefona 1 kez kurun (**hem Ev Wi-Fi hem Mobil Veri açık**, pil kısıtlaması kapalı) ve BIOS'tan `Power On By PCI-E` / `Wake on LAN` (`ErP Ready: Disabled`) açın.
<!-- TE_HW_GUIDE_END -->
