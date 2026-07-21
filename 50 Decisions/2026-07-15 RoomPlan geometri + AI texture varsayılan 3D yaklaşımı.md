---
type: decision
status: accepted
created: 2026-07-15
source: "[[2026-07-16 Oturum Import — 3D Pipeline Evrimi]]"
related: []
---

# Varsayılan 3D yaklaşımı: RoomPlan geometri + AI texture (ARKit mesh offline)

## Bağlam
14.07'de gsplat yerine geçen ARKit Scene Reconstruction (mesh+texture) güzel sonuç verdi ("harika sonuç!") ama tarama sırasında ciddi ısınma ve crash'lere yol açtı; video kaydı + mesh + RoomPlan aynı anda cihazı zorluyordu.

## Karar
Kurucu (15.07):
1. Video kaydı/kare seçimi tarama akışından **tamamen kaldırıldı**.
2. ARKit mesh sistemi **offline moda** alındı (`sceneReconstruction = .none`; kod silinmedi, bayrakla geri açılabilir — `arkitMeshEnabled=false`).
3. Varsayılan 3D görünüm: **RoomPlan geometrisi + fotoğraftan AI texture** (GPT-4o Vision analiz + texture üretimi) + gerçek .usdz mobilyalar.
4. Tarama sırasında yalnızca RoomPlan çalışır; ağır işler (analiz, texture) tarama **bittikten sonra** yapılır.

## Gerekçe
Isınma/crash'i kökten azaltmak; temiz RoomPlan geometrisi + gerçekçi texture kombinasyonunun "döndürülebilir gerçekçi oda" hedefine yetmesi.

## Sonuçlar (Consequences)
- ARKit mesh deneyi değerli ve geri açılabilir durumda: bkz. [[ARKit Scene Reconstruction mesh + texture]].
- Bu karar, not: 14.07 tarihli "varsayılan = ARKit Scene Reconstruction" kararının üzerine yazan **evrimdir** (bir gün sonra pratik sorunlar nedeniyle).
- Render tarafında bu yaklaşım 16.07'de Blender pipeline'ına bağlandı: [[2026-07-16 Render Modal üzerinde headless Blender]].

## İlgili Bilgi
[[Room Scanning Approaches]], [[3D Render Pipeline]]

## Kaynak
[[2026-07-16 Oturum Import — 3D Pipeline Evrimi]] (15.07 mesajları)
