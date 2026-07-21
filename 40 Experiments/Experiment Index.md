---
type: experiment-index
status: living
updated: 2026-07-20
---

# Experiment Index

> Tüm deneylerin listesi. Yeni deney için `00 System/Templates/Experiment Template` kullan. **Başarısız deneyler gizlenmez.**

## Aktif Deneyler
- [[Blender mimari render Modal]] — Faz 3; gerçek veri testleri sürüyor
- [[Texture üretimi generic flux vs fotoğraftan kırpma]] — fotoğraftan kırpma aktif; yakın çekim akışı doğrulama bekliyor

## Rafta / Süperseded Deneyler
> Değerli bilgi — burada tutulur, kod silinmedi.
- [[Gaussian Splatting self-hosted gsplat]] — BAŞARISIZ → rafta (14 Tem). ARKit pozları 3DGS için yetersiz (COLMAP teşhisiyle kanıtlı); COLMAP da texture'sız duvarlarda %1-20 register.
- [[ARKit Scene Reconstruction mesh + texture]] — ÇALIŞTI ama ısınma/crash nedeniyle offline (15 Tem); bayrakla geri açılabilir.
- [[Fotogerçekçi render denemeleri gpt-image-1 ControlNet]] — geometri sadakati sağlanamadı; yerini Blender aldı (16 Tem).

## Özet Tablo

| Deney | Dönem | Durum | Sonuç |
|---|---|---|---|
| [[Gaussian Splatting self-hosted gsplat]] | 10-14 Tem | Rafta | Başarısız (poz kalitesi) |
| [[ARKit Scene Reconstruction mesh + texture]] | 14-15 Tem | Offline (bayrak) | Çalıştı; ısınma/crash |
| [[Fotogerçekçi render denemeleri gpt-image-1 ControlNet]] | 15-16 Tem | Superseded | Geometri sadakati yok |
| [[Blender mimari render Modal]] | 16 Tem → | **Aktif** | Çalışıyor; test sürüyor |
| [[Texture üretimi generic flux vs fotoğraftan kırpma]] | 18 Tem → | **Aktif** | Kırpma çalıştı; regresyona açık |

## Not
Kurulum brief'indeki "birkaç yaklaşım denendi, bazıları kısmen çalıştı, bazıları başarısız" ifadesinin somut karşılığı yukarıdaki tablodur. Bkz. [[Room Scanning Approaches]].
