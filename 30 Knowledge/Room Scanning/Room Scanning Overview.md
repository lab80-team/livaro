---
type: knowledge
status: living
updated: 2026-07-20
related: []
---

# Room Scanning Overview

> Oda tarama çalışmasının merkezi bilgi notu. Deney detayları [[Experiment Index]]'te; bu not mevcut anlayışın özetidir.

## Şu An Bilinenler
- Tarama **Apple RoomPlan** ile yapılıyor (LiDAR'lı iPhone). RoomPlan güvenilir şekilde veriyor: duvarlar/kapılar/pencereler/mobilyalar (her biri 4x4 transform + dimensions), oda ölçüleri.
- Akış (20 Tem itibarıyla): **Oda tara (RoomPlan) → 4-8 köşe fotoğrafı (manuel, AVCapturePhoto) → [planlandı: zemin + duvar yakın çekim, isteğe bağlı] → kayıt → GPT-4o materyal analizi → texture üretimi → 3D oda**. Kurucu teyidi (2026-07-24): mevcut tarama adımları **şimdilik kalıyor**, ileride değişebilir.
- Görselleştirme iki yolla: cihazda canlı RealityKit sahnesi ("Roomplan" sekmesi) + Modal'da Blender render/USDZ ("Render" sekmesi). Bkz. [[3D Render Pipeline]].
- İşlem dağılımı: tarama ve canlı sahne **cihazda**; texture üretimi ve render **sunucuda** (backend + Modal). Ağır iş tarama sırasında değil, sonrasında yapılır (ısınma dersi).
- Fotogerçekçi "gezilebilir" model (3DGS/mesh) denemeleri rafta; bugünkü hedef ölçülere sadık, texture'lı temiz model. Yaklaşım geçmişi: [[Room Scanning Approaches]].

## Varsayımlar
- Oda tarama + gerçek ölçülü görselleştirme, ürünün farklılaştırıcısı — **Needs Validation** (kullanıcı testi yapılmadı).
- Kullanıcılar 4 köşe + yakın çekim fotoğraflarını çekmeye istekli olur — **Needs Validation**.

## Bilinmeyenler
- ~~LiDAR'sız cihazlar için ne yapılacağı~~ — **KARARLAŞTI (2026-07-24)**: MVP yalnızca LiDAR'lı iPhone; LiDAR'sız çözüm (video'dan ölçüm veya başka teknoloji) ileride araştırılacak → [[2026-07-24 MVP yalnızca LiDAR'lı iPhone]]. Manuel fallback (elle ölçü girişi) PM önerisi olarak masada, karar yok.
- MVP'de "dolu odayı dijital boşaltma" (taranan mobilyaları çıkarıp temiz oda gösterme) nasıl yapılacak — **To Be Decided** → [[2026-07-24 MVP tasarım kapsamı — oda boşaltılır, sıfırdan tasarım]].
- Kabul edilebilir minimum doğruluk/kalite çıtası — **Unknown** (dış kullanıcı testi yok).
- RoomPlan yanlış algılarını (TV=pencere) kullanıcının düzeltebileceği bir araç gerekip gerekmediği — **Open Question**.

## Önemli Sorular
- Tarama UX'i ilk kullanıcı için ne kadar akıcı (adım sayısı arttı: tarama + 4 foto + 2 yakın çekim)?
- Otomatik yöntem başarısız olduğunda kullanıcı deneyimi ne olur?

## İlgili Notlar
[[Room Scanning Approaches]], [[3D Render Pipeline]], [[System Architecture]], [[60 Planning/Product Flows|Product Flows]]

## Kaynaklar
[[2026-07-16 Oturum Import — 3D Pipeline Evrimi]], [[2026-07-20 Oturum Import — Texture Pipeline ve Yakın Çekim]], [[2026-07-19 Proje Kurulum Brief]]
