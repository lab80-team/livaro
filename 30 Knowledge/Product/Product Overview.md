---
type: knowledge
status: living
updated: 2026-07-20
related: []
---

# Product Overview

## Şu An Bilinenler
- Ürün, bir **online mobilya pazaryeri** girişimi. Çalışan vizyon cümlesi (kod reposu `PROJECT_STATUS.md`, 16 Tem): **"LiDAR oda tarama (RoomPlan) → AI iç mimarlık tasarımı (GPT-4o) → gerçek ölçülü 3D görselleştirme → ürün satışı"**.
- **Prototype mevcut ve kapsamı belli**: iOS uygulaması (LiDAR'lı iPhone) + NestJS backend. Çalışan uçtan uca akış: oda tarama → köşe fotoğrafları → materyal analizi → texture'lı 3D oda → AI Designer wizard'ı (tarz/bütçe; pgvector ürün arama + GPT-4o yerleşim) → tasarım sonucu (gerçek .usdz mobilyalarla 3D sahne) → Blender render galerisi + USDZ.
- Ayrıştırıcı iddia: tasarım **gerçek oda ölçülerine sadık** (generatif "güzel ama alakasız görsel" yaklaşımı bilinçli terk edildi — bkz. [[2026-07-16 Render Modal üzerinde headless Blender]]).
- Ürün kataloğu şu an yalnızca 3 test ürünü (18 ürün bilinçli silindi; Tripo3D pipeline'ı hazır ama gerçek katalog doldurulmadı).

## Varsayımlar
- Oda tarama + gerçek ölçülü görselleştirme, ürünün farklılaştırıcısı — **Needs Validation** (hiç dış kullanıcıya test edilmedi).
- "Kendi odam" hissi (fotoğraftan birebir texture) satın alma güvenini artırır — **Needs Validation**.

## Bilinmeyenler
- ~~İlk ürünün kapsamı~~ — **KARARLAŞTI (2026-07-21)**: görselleştirme + lead; checkout ileride → [[2026-07-21 İlk ürün kapsamı görselleştirme + lead]]. MVP'nin tam özellik listesi ve lead aksiyonunun tanımı hâlâ **To Be Decided**.
- İlk kullanıcılar ve çözülen ana problem — **To Be Decided** (bkz. [[Target Users]], [[User Problems]]).
- Gelir modeli detayı (komisyon/lead ücreti/abonelik) — **To Be Decided** (bkz. [[Marketplace Model]]).
- LiDAR'lı iPhone zorunluluğunun pazar daraltması nasıl ele alınacak — **Open Question**.

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
