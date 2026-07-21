---
type: decision
status: accepted
created: 2026-07-16
source: "[[2026-07-16 Oturum Import — 3D Pipeline Evrimi]]"
related: []
---

# Fotogerçekçi çıktı yolu: Modal'da headless Blender (Faz 3)

## Bağlam
Fotogerçekçi tasarım görseli için sırasıyla GPT-4o image generation (metin prompt → kat planı PNG referansı → iki aşamalı analiz) ve Replicate ControlNet (RealityKit snapshot + img2img) denendi; hiçbiri oda geometrisine/ölçülere güvenilir şekilde sadık kalamadı.

## Karar
Kurucu (16.07, "Faz 3'e başlıyoruz"): Fotogerçekçi çıktı **programatik** üretilir — Modal'da headless **Blender 4.2** (Cycles GPU, T4): RoomPlan JSON → duvar (15cm) / kapı boşluğu / pencere+cam / zemin poligonu / PBR materyaller / mobilya GLB'leri / ışıklar / 4 kamera (izometrik, eye-level, top, bird-eye; dollhouse tekniği) → 4× PNG (2048) + `room.glb` + `room.usdz` → R2.

## Gerekçe
Generatif modeller ölçü/geometri korumada güvenilmez; Blender geometrik olarak %100 doğru, deterministik ve ölçülere sadık.

## Sonuçlar (Consequences)
- Endpoint: `POST /design-results/:id/render-blender`; iOS 5 sn polling → galeri + USDZ QuickLook.
- Eski gpt-image-1 yolu (`POST /design-results/:id/render`) kodda duruyor ama iOS artık Blender yolunu kullanıyor (akıbeti açık soru).
- Cycles çıktısı "temiz ama CG" — istenirse üstüne img2img güzelleştirme katmanı eklenebilir (opsiyonel; `_enhance_render` flux img2img adımı mevcut).

## İlgili Bilgi
[[3D Render Pipeline]], [[Blender mimari render Modal]], [[Fotogerçekçi render denemeleri gpt-image-1 ControlNet]]

## Kaynak
[[2026-07-16 Oturum Import — 3D Pipeline Evrimi]] (16.07 mesajları)
