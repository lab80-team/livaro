---
type: decision
status: accepted
created: 2026-07-14
source: "[[2026-07-16 Oturum Import — 3D Pipeline Evrimi]]"
related: []
---

# Gaussian Splatting rafa kaldırıldı

## Bağlam
Haftalarca süren gsplat çalışması (koordinat deneyleri, COLMAP teşhisi, video tabanlı kare seçimi, depth/point-cloud planları) kabul edilebilir kalitede oda splat'ı üretemedi. COLMAP teşhisi ARKit pozlarının 3DGS için yetersiz olduğunu kanıtladı; COLMAP da texture'sız duvarlarda %1-20 register'da kaldı; ARKit+LiDAR fallback eğitimi teknik olarak çalıştı ama kalite KIRI'nin altında.

## Karar
Kurucu (14.07): "Gaussian Splatting pipeline'ını durdur — haftalardır çalışmıyor." Varsayılan 3D görünüm artık splat değil. **Kod silinmez, dokunulmaz** — ileride geri dönülebilir (rafta).

## Gerekçe
Zaman maliyeti; cihaz-üstü/ucuz alternatiflerin (ARKit Scene Reconstruction, sonrasında RoomPlan+AI texture) anında sonuç vermesi.

## Sonuçlar (Consequences)
- `gsplat/`, `src/splat/`, MetalSplatter viewer ve Modal app çalışır durumda bekliyor; `USE_COLMAP` default true.
- Aynı gün ARKit Scene Reconstruction'a geçildi; o da 15.07'de offline'a alındı → bkz. [[2026-07-15 RoomPlan geometri + AI texture varsayılan 3D yaklaşımı]].

## İlgili Bilgi
[[Gaussian Splatting self-hosted gsplat]], [[Room Scanning Approaches]]

## Kaynak
[[2026-07-16 Oturum Import — 3D Pipeline Evrimi]] (14.07 mesajı)
