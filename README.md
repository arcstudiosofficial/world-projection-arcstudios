# World Projection

**Dünyanın önümüzdeki 25 yılı — 2026’dan 2050’ye, yıl yıl gelecek modeli**
*The next 25 years of our world — a future model from 2026 to 2050, year by year*

**ARC Studios** · **Emre Arıcı** — Tam Bağımsız Fikir Stüdyosu · [arcstudios.com.tr](https://arcstudios.com.tr)

🇹🇷 Türkçe · 🇬🇧 English · 🇩🇪 Deutsch · 🇷🇺 Русский · 🇨🇳 中文 · 🇪🇸 Español

---

## TR

2026’dan 2050’ye dünyanın nasıl değişebileceğini gösteren etkileşimli 3D küre ve 3D şehir deneyimi. Ülke veya şehir seç, yılı ve senaryoyu (İyimser / Orta / Kötümser) belirle; önce o yere özel brifingi oku, sonra değişimi 3D olarak izle.

### Özellikler
- **6 dil:** Türkçe, İngilizce, Almanca, Rusça, Çince, İspanyolca. Arayüz, brifingler, yıl açıklamaları, şehir notları ve kilometre taşları dahil her şey çevrildi. Dil, açılış ekranından veya sol üstteki menüden değişir; seçim hatırlanır. Bağlantıyla dil seçmek için: `?lang=en`
- **Müzikli açılış ekranı:** tarayıcıda gerçek zamanlı üretilen sinematik müzik (ses dosyası yok); 🔊 düğmesiyle açılıp kapanır
- **3D küre:** iklim, nüfus, ekonomi, enerji, teknoloji, din, kent ve göç katmanları
- **70 şehir:** 58’inde şehre özel iklim verisi ve “2050 iklim ikizi”, 43’ünde BM şehir nüfusu projeksiyonu
- **3D şehir modu:** gerçek kıyı şeridi (Natural Earth 10m), gün/gece döngüsü, fiziksel gökyüzü, dalgalı deniz; yıla ve senaryoya göre ısı dalgalanması, kuraklık, orman yangını dumanı, yağmur/toz, deniz yükselişi, güneş panelleri, rüzgâr türbinleri, elektrikli araçlar ve dronlar
- **Yıla, senaryoya ve yere göre değişen brifing** ve kilometre taşları
- Three.js **r187**, `WebGPURenderer` + **TSL** (WebGPU yoksa otomatik WebGL2), `RenderPipeline`, GPU compute

### Çalıştırma
Tek dosya: `index.html`. Herhangi bir statik sunucuda çalışır (Three.js jsDelivr CDN’den yüklenir).

```bash
npx serve .            # veya: python3 -m http.server
```
WebGL2 modunu zorlamak için adresin sonuna `#webgl` ekle.

### Kaynaktan derleme
```bash
npm install
npm run build          # src/ → index.html
npm run grids          # (isteğe bağlı) şehir kıyı maskelerini yeniden üret
npm run climate -- path/to/future_cities_data.csv   # (isteğe bağlı) şehir iklimini yeniden eşle
```
- `src/src.html` — arayüz, küre, brifing
- `src/city3d.js` — 3D şehir modu
- `src/data.js` — senaryolar, ülke/şehir verileri, kilometre taşları (Türkçe temel metin)
- `src/i18n/*.js` — dil paketleri (`tr`, `en`, `de`, `ru`, `zh`, `es`)
- `src/splash.js` — açılış ekranı ve Web Audio müziği
- `src/names_all.json`, `src/grids.json`, `src/cityclim.json` — üretilmiş veri

**Yeni dil eklemek:** `src/i18n/en.js` dosyasını kopyala, metinleri çevir, `scripts/build.js` ve `src/src.html` içindeki `LANGS` listesine dil kodunu ekle.

### Cloudflare Pages ile yayın (arcstudios.com.tr)
1. Cloudflare → Workers & Pages → Create → Pages → **Connect to Git** → bu repo
2. Framework preset: **None** · Build command: *(boş)* · Output directory: `/`
3. Custom domain: örn. `worldprojection.arcstudios.com.tr`

### Uyarı
Değerler yaklaşık projeksiyonlardır, kesin tahmin değildir. 3D şehirlerde binalar ve yollar prosedüreldir; deniz yükselişi görsel olarak ×25 abartılmıştır. Kaynaklar: [DATA_SOURCES.md](DATA_SOURCES.md).

---

## EN

An interactive 3D globe and 3D city experience showing how the world may change from 2026 to 2050 — climate, population, economy, energy, technology, religion and urbanisation — under three SSP-based scenarios. Pick a country or city, a year and a scenario, read a briefing written for that place, then watch the change in 3D.

- 6 languages (TR, EN, DE, RU, ZH, ES) — everything is translated, including briefings, city notes and milestones. Deep link: `?lang=en`
- Cinematic splash screen with music generated live in the browser (Web Audio, no audio files)
- Single-file `index.html`, Three.js r187 WebGPU + TSL with automatic WebGL2 fallback

Code: MIT. Data: see [DATA_SOURCES.md](DATA_SOURCES.md) (city climate data CC BY 4.0, Bastin et al. 2019).

---

© 2026 Emre Arıcı / ARC Studios
