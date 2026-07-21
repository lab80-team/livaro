---
type: knowledge
status: living
updated: 2026-07-20
related: []
---

# Room Scanning Approaches

> Denenen ve düşünülen oda tarama/görselleştirme yaklaşımları. Detaylar deney notlarında ([[Experiment Index]]). Başarısız yaklaşımlar **silinmez** — değerli bilgidir.

## Denenen Yaklaşımlar

| Yaklaşım | Durum | Sonuç Özeti | Deney/Karar |
|---|---|---|---|
| RoomPlan (Apple) geometri taraması | **Aktif — temel** | Duvar/kapı/pencere/obje + ölçüler güvenilir; render yalnızca saf Transform(matrix:) ile | [[2026-07-09 3D render saf Transform matrix kullanır]] |
| Gaussian Splatting (self-hosted gsplat) | Rafta | ARKit pozları 3DGS'e yetmiyor (COLMAP kanıtı); texture'sız duvarda COLMAP %1-20 register; kalite < KIRI | [[Gaussian Splatting self-hosted gsplat]], [[2026-07-14 Gaussian Splatting rafa kaldırıldı]] |
| ARKit Scene Reconstruction (mesh+texture) | Offline (bayrak) | Teknik olarak çalıştı ("harika sonuç"); ısınma/crash → kapatıldı | [[ARKit Scene Reconstruction mesh + texture]] |
| RoomPlan geometri + fotoğraftan AI texture | **Aktif — varsayılan** | Köşe (+yakın çekim) fotoğraflarından kırpılan texture RoomPlan geometrisine uygulanır | [[2026-07-15 RoomPlan geometri + AI texture varsayılan 3D yaklaşımı]], [[Texture üretimi generic flux vs fotoğraftan kırpma]] |
| Generatif render (gpt-image-1 / ControlNet) | Superseded | Ölçü/geometri sadakati sağlanamadı → Blender'a geçildi | [[Fotogerçekçi render denemeleri gpt-image-1 ControlNet]] |
| Modal'da headless Blender render | **Aktif — render yolu** | Ölçülere sadık 4 açı PNG + GLB + USDZ | [[Blender mimari render Modal]] |

## Bilinen Sınırlar
- RoomPlan büyük TV/ekranı pencere sanabiliyor (veri sorunu; bkz. [[Known Pitfalls]]).
- Eski taramalarda transform/dimensions eksik → render edilemez, yeniden tarama gerekir.
- Manuel fotoğrafların pose'u yok → duvar↔fotoğraf eşleşmesi yapılamıyor; tek baskın duvar texture'ı.

## Önemli Sorular
- Manuel fallback (kullanıcının odayı elle çizmesi/düzeltmesi) gerekecek mi? — **To Be Decided** (LiDAR'sız cihazlar kapsam dışı mı?)
- ARKit mesh geri açılmalı mı (tarama-sonrası işleme ile ısınma aşılabilir mi)? — **Open Question**

## İlgili Notlar
[[Room Scanning Overview]], [[3D Render Pipeline]], [[Experiment Index]]

## Kaynaklar
[[2026-07-16 Oturum Import — 3D Pipeline Evrimi]], [[2026-07-20 Oturum Import — Texture Pipeline ve Yakın Çekim]], [[2026-07-19 Proje Kurulum Brief]]
