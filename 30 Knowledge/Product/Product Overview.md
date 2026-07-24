---
type: knowledge
status: living
updated: 2026-07-24
related: []
---

# Product Overview

## Şu An Bilinenler
- Ürün, bir **online mobilya pazaryeri** girişimi. Çalışan vizyon cümlesi (kod reposu `PROJECT_STATUS.md`, 16 Tem): **"LiDAR oda tarama (RoomPlan) → AI iç mimarlık tasarımı (GPT-4o) → gerçek ölçülü 3D görselleştirme → ürün satışı"**.
- **Uçtan uca vizyon anlatıldı (2026-07-24 thinking session)**: kullanıcı odasını tarar, bütçe+tarz+isteklerini verir; AI mağazaların **gerçek ürünleriyle** odayı tasarlar; 3D+2D incelenir; sepete eklenir, tek yerden satın alınır; Livaro operasyonun tamamında (ödeme, teslimat koordinasyonu, iade) aracı — "Amazon gibi pazaryeri". Ayrıştırıcı: mevcut iç mimari uygulamaları hayali ürün gösterir, Livaro gerçek/satın alınabilir ürün yerleştirir. Kaynak: [[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu]].
- **Uzun vade özellikleri (fikir aşaması)**: 2D fotoğraflardan video walkthrough; Marble benzeri fotoğraftan sanal dünya (abonelik veya tek kullanımlık satış); ünlü tasarımları satışı (ünlünün zevkine göre AI tasarım); chat ile tasarım değişikliği; dolu odada parça değiştirme; LiDAR'sız cihaz desteği.
- **Prototype mevcut ve kapsamı belli**: iOS uygulaması (LiDAR'lı iPhone) + NestJS backend. Çalışan uçtan uca akış: oda tarama → köşe fotoğrafları → materyal analizi → texture'lı 3D oda → AI Designer wizard'ı (tarz/bütçe; pgvector ürün arama + GPT-4o yerleşim) → tasarım sonucu (gerçek .usdz mobilyalarla 3D sahne) → Blender render galerisi + USDZ.
- Ayrıştırıcı iddia: tasarım **gerçek oda ölçülerine sadık** (generatif "güzel ama alakasız görsel" yaklaşımı bilinçli terk edildi — bkz. [[2026-07-16 Render Modal üzerinde headless Blender]]).
- Ürün kataloğu şu an yalnızca 3 test ürünü (18 ürün bilinçli silindi; Tripo3D pipeline'ı hazır ama gerçek katalog doldurulmadı).

## Varsayımlar
- Oda tarama + gerçek ölçülü görselleştirme, ürünün farklılaştırıcısı — **Needs Validation** (hiç dış kullanıcıya test edilmedi).
- "Kendi odam" hissi (fotoğraftan birebir texture) satın alma güvenini artırır — **Needs Validation**.

## Bilinmeyenler
- ~~İlk ürünün kapsamı~~ — **KARARLAŞTI (2026-07-21, güncellendi 2026-07-24)**: görselleştirme + **sepet MVP'de; checkout ödeme teknolojisi seçilince** → [[2026-07-24 Sepet MVP'de, checkout ödeme teknolojisi seçilince]]. MVP tasarım kapsamı → [[2026-07-24 MVP tasarım kapsamı — oda boşaltılır, sıfırdan tasarım]]. Checkout gelene kadar sepetin davranışı **To Be Decided**.
- ~~Hedef kullanıcı anı~~ — **KARARLAŞTI (2026-07-21, teyit 2026-07-24)**: taşınma + tadilat/yenileme; tek parça alım ileriki sürüme ertelendi → [[2026-07-21 Hedef kullanıcı anı — taşınma ve tadilat]].
- ~~Çözülen ana problem~~ — **Kurucu hipotezi netleşti (2026-07-24)** → [[User Problems]]; dış doğrulama yok.
- ~~Gelir modeli~~ — **Plan netleşti (2026-07-24)**: kısa vade %10 komisyon, orta vade reklam (Sponsorlu etiketli), uzun vade indirim/hizmet bedeli → [[Marketplace Model]].
- ~~LiDAR stratejisi~~ — **KARARLAŞTI (2026-07-24)**: MVP yalnızca LiDAR'lı iPhone; LiDAR'sız çözüm ileride araştırılacak → [[2026-07-24 MVP yalnızca LiDAR'lı iPhone]].
- İlk kullanıcıların tam profili ve edinme kanalı — **To Be Decided** (bkz. [[Target Users]]).

## Önemli Sorular
- En küçük değerli ilk ürün (MVP) nedir? Teknoloji demosu değil, kimin hangi işini görüyor?
- Bkz. [[Open Questions]]

## İlgili Notlar
- [[Product Principles]]
- [[60 Planning/Product Flows|Product Flows]]
- [[Marketplace Model]]
- [[Room Scanning Overview]]
- [[System Architecture]]

## Kaynaklar
- [[2026-07-19 Proje Kurulum Brief]]; `~/Desktop/livaro/PROJECT_STATUS.md`
- [[2026-07-16 Oturum Import — 3D Pipeline Evrimi]], [[2026-07-20 Oturum Import — Texture Pipeline ve Yakın Çekim]]
