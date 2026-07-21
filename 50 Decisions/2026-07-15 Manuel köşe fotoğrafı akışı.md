---
type: decision
status: accepted
created: 2026-07-15
source: "[[2026-07-16 Oturum Import — 3D Pipeline Evrimi]]"
related: []
---

# Fotoğraflar kullanıcı tarafından manuel çekilir (otomatik kare yakalama kaldırıldı)

## Bağlam
Texture/analiz için fotoğraf kaynağı olarak otomatik ARKit kare yakalama (video kaydı + en iyi kare seçimi) kullanılıyordu; ısınma/crash'e katkı veriyordu ve kare kalitesi kontrolsüzdü.

## Karar
Kurucu (15.07): Tarama bittikten sonra ayrı bir ekranda (`RoomPhotoCaptureView`) kullanıcı **kendisi fotoğraf çeker**: AVCapturePhoto ile, köşe rehber ikonu eşliğinde **min 4 / max 8 köşe fotoğrafı**; 4 köşe tamamlanınca "Devam Et" aktif olur. Otomatik kare yakalama kodu akıştan tamamen kaldırıldı.

## Gerekçe
Yüksek çözünürlüklü, net, stabil fotoğraflar; tarama sırasındaki CPU/GPU yükünün azalması; kullanıcıya kontrol.

## Sonuçlar (Consequences)
- Köşe fotoğrafları backend'e base64 gönderilir; R2'de `room-textures/{scanId}/src_i.jpg` olarak saklanır.
- GPT-4o materyal analizi ve texture üretimi bu fotoğraflardan beslenir.
- 18-19 Tem'de akışa isteğe bağlı yakın çekim adımları eklenmesi planlandı: [[2026-07-19 Tarama akışına zemin-duvar yakın çekim adımları]].

## İlgili Bilgi
[[Room Scanning Overview]], [[3D Render Pipeline]]

## Kaynak
[[2026-07-16 Oturum Import — 3D Pipeline Evrimi]] (15.07 mesajı)
