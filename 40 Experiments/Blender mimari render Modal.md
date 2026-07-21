---
type: experiment
status: active
owner: "[[Selim]]"
created: 2026-07-16
related: []
---

# Blender mimari render (Modal) — Faz 3

## Soru
RoomPlan verisinden Modal'da headless Blender ile ölçülere sadık, gerçekçi render + USDZ üretilebilir mi?

## Hipotez
Programatik Blender sahnesi (geometri %100 doğru) + fotoğraftan texture + Cycles, generatif yaklaşımların başaramadığı ölçü sadakatini sağlar.

## Kurulum
`blender/modal_blender.py` (Blender 4.2, Cycles GPU T4) + `blender/room_to_blender.py` (bpy; ARKit Y-up → Blender Z-up). Payload: walls/doors/windows/floorPolygon/furniture (+texture URL'leri, resolution 2048, samples 256). Çıktı: 4× PNG + room.glb + room.usdz → R2 `blender-rooms/{designId}/`.

## Sonuç (devam ediyor — 20 Tem itibarıyla)
- **Çalıştı**: 4×5 m test odası uçtan uca (4 render + glb + usdz); gerçek oda render'ları alınıyor; 1 birim = 1 m ölçek doğrulandı (oda küçültülmüyor); tavan kaldırıldı; kapı boşluğu + çift kanat panel + kol; pencere + cam; dollhouse tekniği; görünmez beyaz platform + gölge (maket hissi).
- **Kısmen / sorunlu**:
  - Texture pipeline regresyonlara açık — zemin iki kez "yine kahverengi"ye döndü; kırpma yolu logla/R2 içeriğiyle doğrulanmalı.
  - Pencere görünürlüğü zayıftı (16-17 Tem şikâyeti) — iyileştirildi, gerçek odalarda sürmeli.
  - Mobilya min-oran fit ölçek algısı bozabiliyor; Tripo GLB rotasyon işareti doğrulanmadı.
  - RoomPlan'ın TV'yi pencere sanması → çıktıda hayalet cam panel (veri sorunu).
- **Test bekliyor**: girintili odada `floorPolygon` zincirleme; yakın çekim akışıyla uçtan uca cihaz testi; Blender USDZ'nin QuickLook materyel uyumu genelinde.

## İşe Yarayan
Ölçü sadakati; deterministik çıktı; 4 kamera galerisi; USDZ QuickLook.

## Başarısız Olan
- USDZ viewer'da kamera elevation kısıtı (QuickLook'ta imkânsız; custom viewer denemeleri beğenilmedi, 4 commit revert — 18 Tem).

## Karar / Sonuç
Aktif yol: [[2026-07-16 Render Modal üzerinde headless Blender]]. Devamı: [[2026-07-19 Tarama akışına zemin-duvar yakın çekim adımları]].

## İlgili Kod / Branch
`blender/`, `src/design-result/`; deploy: `python3 -m modal deploy blender/modal_blender.py`.

## İlgili Kaynak
[[2026-07-16 Oturum Import — 3D Pipeline Evrimi]], [[2026-07-20 Oturum Import — Texture Pipeline ve Yakın Çekim]]
