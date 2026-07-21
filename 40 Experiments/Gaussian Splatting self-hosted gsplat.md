---
type: experiment
status: shelved
owner: "[[Selim]]"
created: 2026-07-10
related: []
---

# Gaussian Splatting (self-hosted gsplat)

## Soru
Oda taramasından fotogerçekçi, gezilebilir bir 3D model (3DGS) üretilebilir mi — kendi pipeline'ımızla, 3. parti API'siz?

## Hipotez
ARKit/RoomPlan zaten kamera pozları veriyor; COLMAP'siz, bilinen pozlarla gsplat eğitimi hızlı (~$0.5/sahne) ve yeterli kalitede olur.

## Yaklaşım / Kurulum
- Render: **MetalSplatter** (SPM) + `GaussianSplatTestView.swift`; örnek splat ile doğrulandı.
- Capture: tarama sırasında kare + pose (4x4) + intrinsics (fx,fy,cx,cy) kaydı; önce 0.5 sn örnekleme (blur+motion filtre), sonra **video tabanlı** (AVAssetWriter 30 FPS + Laplacian keskinlik + 5cm/10° hareket filtresi ile en iyi 200-300 kare).
- Eğitim: Modal T4'te nerfstudio **splatfacto** (`gsplat/modal_app.py`); backend `src/splat/`; R2 + presigned .ply → MetalSplatter.
- KIRI Engine API teklifi reddedildi → [[2026-07-11 Splat için 3. parti API yasak]].

## Sonuç: BAŞARISIZ → RAFA KALDIRILDI (14 Tem)
- ARKit pozlarıyla tüm eğitimler "bulanık ve dağınık / tam garbage".
- Koordinat dönüşüm deneyleri (OpenCV flip, cy→h-cy, JPEG dikey flip) **hepsi başarısız** — sorun konvansiyon değildi.
- **COLMAP teşhisi (kesin kanıt)**: aynı karelerle COLMAP pozları yapılı sonuç verdi → ARKit/RoomPlan pozları 3DGS için yetersiz. Ama COLMAP de texture'sız düz duvarlarda karelerin yalnızca %1-20'sini register edebildi.
- ARKit+LiDAR fallback (depth point cloud init + SO3xR3 poz optimizasyonu) teknik olarak çalıştı ama kalite **KIRI uygulamasının altında** (KIRI kıyas testi: KIRI düzgün, bizim çıktı çöp).
- Ek maliyet dersi: Modal kredisi tükenip workspace kilitlendi (13 Tem).

## İşe Yarayan
- MetalSplatter render + presigned .ply akışı; Modal eğitim altyapısı; video tabanlı en-iyi-kare seçimi (sonradan ısınma nedeniyle akıştan çıkarıldı); `USE_COLMAP=true` yolu.

## Başarısız Olan
- ARKit pozlarıyla doğrudan eğitim; koordinat flip varyantları; texture'sız duvarlarda COLMAP register.

## Karar / Sonuç
[[2026-07-14 Gaussian Splatting rafa kaldırıldı]] — kod duruyor (dokunulmuyor), varsayılan yol değil.

## Sonraki Adım
(Opsiyonel/rafta) Geri dönülürse: depth map + point cloud init + daha dokulu ortamlarda test. 3. parti API hâlâ yasak.

## İlgili Kod / Branch
`gsplat/modal_app.py`, `src/splat/`, `ios/Livaro/Scene3D/GaussianSplatTestView.swift`

## İlgili Kaynak
[[2026-07-16 Oturum Import — 3D Pipeline Evrimi]]
