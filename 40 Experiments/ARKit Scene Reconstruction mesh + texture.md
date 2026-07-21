---
type: experiment
status: shelved
owner: "[[Selim]]"
created: 2026-07-14
related: []
---

# ARKit Scene Reconstruction (mesh + texture)

## Soru
Cihaz üzerinde, cloud'suz ve anında, gerçekçi bir 3D oda modeli üretilebilir mi (Polycam / 3D Scanner App yaklaşımı)?

## Hipotez
ARKit `sceneReconstruction = .meshWithClassification` (LiDAR mesh) + kamera karelerinden keyframe projeksiyon texture, gsplat'ın yerini tutacak kalitede sonuç verir — $0 maliyet, anında.

## Yaklaşım / Kurulum
- ARMeshAnchor toplama → tarama bitince birleştirilmiş mesh; üçgen başına en iyi keyframe seçimi, UV = görüntüye projeksiyon; RealityKit'te render (orbit/zoom).
- Canlı tarama UX'i: beyaz wireframe (taranmış) + koyu mavi (taranmamış) overlay; Polycam tarzı.
- İyileştirmeler: Laplacian mesh smoothing, boşluk doldurma (komşu renk interpolasyonu), occlusion.
- Dosyalar: `Scene3D/TexturedRoomMesh*.swift`; cihaz-yerel depolama (`Documents/room_meshes/`).

## Sonuç: ÇALIŞTI ama RAFA KALINDI (15 Tem)
- 14 Tem: kurucu değerlendirmesi "**harika sonuç!**" — teknik olarak başarılı.
- 15 Tem: tarama sırasında **ısınma ve crash'ler** (video kaydı + mesh + RoomPlan birlikte cihazı zorladı). Adım adım geri alma sonrası `sceneReconstruction = .none` yapıldı; kod bayrakla duruyor (`arkitMeshEnabled=false`).

## İşe Yarayan
- Mesh + keyframe texture yaklaşımı; canlı wireframe overlay; smoothing/boşluk doldurma.

## Başarısız Olan
- Tarama sırasında RoomPlan + mesh + video birlikte: termal/stabilite sınırı aşıldı.

## Karar / Sonuç
[[2026-07-15 RoomPlan geometri + AI texture varsayılan 3D yaklaşımı]] — ARKit mesh offline; bayrakla geri açılabilir.

## Sonraki Adım
Geri açma kararı açık ([[Open Questions]]): tarama-sonrası (tarama sırasında değil) mesh işleme ile ısınma sorunu aşılabilir mi denenmedi.

## İlgili Kod / Branch
`ios/Livaro/Scene3D/TexturedRoomMesh*.swift`; keyframe yakalama git geçmişinde.

## İlgili Kaynak
[[2026-07-16 Oturum Import — 3D Pipeline Evrimi]]
