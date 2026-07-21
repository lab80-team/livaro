---
type: knowledge
status: living
updated: 2026-07-20
related: []
---

# 3D Render Pipeline

> Taranan odanın görselleştirme zinciri: canlı RealityKit sahnesi + Modal'da Blender render/USDZ. Kaynak: [[2026-07-16 Oturum Import — 3D Pipeline Evrimi]], [[2026-07-20 Oturum Import — Texture Pipeline ve Yakın Çekim]].

## Şu An Bilinenler

### İki ayrı görselleştirme yolu (karıştırma!)
1. **RoomPlan canlı sahnesi** (`RoomScene3DView.swift`, RealityKit nonAR): cihazda anında; saf `Transform(matrix:)` + `generateBox` (bkz. [[2026-07-09 3D render saf Transform matrix kullanır]]); texture'lar PBR olarak uygulanır; AI tasarım ürünleri kutu→usdz değişimiyle gösterilir. UI sekmesi adı: **"Roomplan"**.
2. **Blender çıktısı** (Render sekmesi): Modal'da headless Blender → 4 açı PNG + `room.glb` + `room.usdz` (QuickLook). Bkz. [[2026-07-16 Render Modal üzerinde headless Blender]].
İkisinin karıştırılması 16-18 Tem'de iki kez yanlış dosyada çalışmaya yol açtı — istekte hangi yol olduğunu netleştir.

### Texture pipeline (aktif tasarım)
- Öncelik zinciri: **(1)** zemin/duvar yakın çekim fotoğrafı varsa sabit merkez bölge kırp (`{x:0.1, y:0.1, w:0.8, h:0.8}`) → **(2)** köşe fotoğrafından GPT-4o bbox ile temiz bölge kırp → **(3)** Replicate flux-schnell generic üretim.
- Kırpılan parça **2x2 aynalı karo** (mirror tile) ile seamless'a yaklaştırılır.
- R2 düzeni: `room-textures/{scanId}/walls.jpg`, `floor.jpg`, `manifest.json` (GPT analizi), `src_i.jpg` (köşe fotoğrafları), planda `src_floor.jpg`/`src_wall.jpg` (yakın çekimler).
- GPT-4o `analyzeRoomPhotos`: baskın duvar + zemin (renk hex, materyal tipi, textureDescription, lightingWarmth). Duvar↔fotoğraf eşleşmesi yok (pose'suz manuel çekim) → tek baskın duvar texture'ı tüm duvarlara. `analyzeSurfaces` (yüzey bazlı) kodda var ama bağlı değil.
- Tetikleme **manuel** (client `generate-textures` çağırır); otomatik orkestrasyon yok — çağrılmazsa Blender düz renk fallback'ine düşer.

### Blender sahne kuralları
- Duvar 15 cm; kapı boşluğu + çift kanat kapı paneli + siyah metal kol (18 Tem eklendi); pencere boşluğu + cam; zemin duvar iç kenarlarından zincirlenmiş poligon (kopma eşiği 1.5 m); tavan yok (16 Tem'de kesin kaldırıldı).
- 4 kamera: izometrik / eye-level / top / bird-eye; **dollhouse tekniği** (kameraya bakan duvarlar o render'da gizlenir) + `film_transparent`.
- `_enhance_render` (modal_blender.py): yalnızca eye-level PNG'ye flux img2img güzelleştirme (prompt_strength 0.55); `replicateToken` payload'da yoksa atlanır.
- Mobilya: Tripo GLB'leri cm ölçülerine min-oran fit; `widthCm` yoksa ölçeklenmez (bilinen zayıflık).

### Görüntüleyici (USDZ)
- QuickLook auto-frame; app tarafında ölçek çarpanı yok. Kamera elevation kısıtı QuickLook'ta yapılamıyor; custom viewer denemeleri 18 Tem'de beğenilmedi ve **revert edildi** (4 commit).
- Maket "platform/plaka" denemesi Blender sahnesine eklendi, RoomScene3DView'a yanlışlıkla da eklenip kaldırıldı.

### Bilinen veri sorunu
- RoomPlan, büyük TV/ekranı **pencere** olarak yanlış algılayabiliyor → USDZ'de olmayan cam panel. Blender tarafında çözülemez; farkındalık gerekli (kullanıcıya düzeltme aracı ileride düşünülebilir — **Open Question**).

## Varsayımlar
- Fotoğraftan kırpılan texture + mirror tile, kullanıcının "kendi odam" hissi için yeterli — **Needs Validation** (cihazda uçtan uca test bekliyor).

## Bilinmeyenler
- Yakın çekim akışının cihazda uçtan uca durumu — **Needs Validation**.
- `floorPolygon` zincirleme algoritmasının girintili odalarda doğruluğu — **Needs Validation**.
- Blender USDZ'nin QuickLook'ta materyallerle tam uyumu — kısmen doğrulandı, gerçek odalarda sürmeli.

## Önemli Sorular
- Texture regresyonlarına karşı otomatik doğrulama (örn. render sonrası renk histogram karşılaştırması) kurulmalı mı?
- Süpürgelik, duvar çıtaları gibi detaylar ne zaman eklenmeli (18 Tem'de "şimdi öncelik değil" dendi)?

## İlgili Notlar
[[System Architecture]], [[Blender mimari render Modal]], [[Texture üretimi generic flux vs fotoğraftan kırpma]], [[Known Pitfalls]]

## Kaynaklar
[[2026-07-16 Oturum Import — 3D Pipeline Evrimi]], [[2026-07-20 Oturum Import — Texture Pipeline ve Yakın Çekim]], `~/Desktop/livaro/PROJECT_STATUS.md`
