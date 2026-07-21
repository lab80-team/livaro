---
type: experiment
status: superseded
owner: "[[Selim]]"
created: 2026-07-15
related: []
---

# Fotogerçekçi render denemeleri (gpt-image-1 / ControlNet)

## Soru
AI görüntü üretimiyle, gerçek oda ölçülerine/geometrisine sadık fotogerçekçi tasarım görseli üretilebilir mi?

## Hipotez
RoomPlan verisi + kullanıcı fotoğrafı + iyi prompt ile GPT-4o/gpt-image-1 (veya ControlNet) ölçülere uyan render üretir.

## Yaklaşım (denenen varyantlar, sırayla)
1. **Metin prompt** (ölçüler yazıyla) → GPT-4o image gen: ölçüleri anlamadı.
2. **Kat planı PNG kontrol referansı** (programatik SVG/sharp — `floor-plan-renderer.ts`) + köşe fotoğrafı + metin: yetersiz.
3. **İki aşamalı**: önce GPT-4o Vision "odayı anla" (JSON oda kimliği — `analyzeRoomIdentity`, R2 önbellekli) → sonra tasarım render: yetersiz.
4. **MeltFlex tarzı**: RealityKit snapshot (geometrik doğru) + Replicate ControlNet (flux-canny) img2img: geometri korunumu hâlâ güvenilmez.
5. **gpt-image-1 + kurucunun kapsamlı Türkçe sistem prompt'u** (`src/design-result/render-prompt.ts`; "geometriyi ASLA bozma…"): yol kodda duruyor.

## Sonuç: KISMEN — yerini Blender'a bıraktı (16 Tem)
Hiçbir generatif varyant duvar/kapı/pencere yerleşimini ve ölçüleri güvenilir korumadı. Karar: fotogerçekçi çıktı programatik üretilir → [[2026-07-16 Render Modal üzerinde headless Blender]].

## İşe Yarayan
- `analyzeRoomIdentity` (oda kimliği JSON'u) ve kat planı renderer'ı kodda kaldı, başka amaçlarla kullanılabilir.
- Kurucunun render sistem prompt'u `render-prompt.ts`'te duruyor.

## Başarısız Olan
- Generatif modellerin ölçü/geometri sadakati (tüm varyantlarda).

## Karar / Sonuç
Süperseded: aktif yol Blender; generatif katman yalnızca opsiyonel güzelleştirme (`_enhance_render` img2img).

## İlgili Kod / Branch
`src/design-result/render-prompt.ts`, `floor-plan-renderer.ts`; eski endpoint `POST /design-results/:id/render` (akıbeti açık soru).

## İlgili Kaynak
[[2026-07-16 Oturum Import — 3D Pipeline Evrimi]]
