---
type: planning
status: living
updated: 2026-07-28
aliases: ["Product Flows (Planning)"]
---

# Product Flows (Planning)

> Tasarlanması gereken akışlar ve durumları. Durum etiketleri: **Not explored → Exploring → Defined → Prototype → Implemented → Validated**.
>
> Not: Ticari modelin doğrudan checkout olduğu **varsayılmaz** — "Checkout or lead generation" akışı bilinçli olarak açık bırakılmıştır (bkz. [[Marketplace Model]]).
>
> "Prototype" = prototipte çalışıyor; hiçbir akış dış kullanıcıyla **Validated** değil.

| Akış | Durum | Not |
|---|---|---|
| User registration | Prototype | JWT auth mevcut (prototipte giriş yapılıyor); tasarımı/onboarding'i düşünülmedi. Bkz. [[User Onboarding]] |
| User onboarding | Not explored | Bkz. [[User Onboarding]] |
| Room creation | Prototype | "Projelerim" + oda detay ekranları mevcut |
| Room scanning | Prototype | RoomPlan + 4-8 köşe foto (+ planda yakın çekimler); bkz. [[Room Scanning Overview]] |
| Manual room setup | Not explored | Otomatik taramaya fallback; LiDAR'sız cihaz sorusuyla bağlantılı |
| Furniture discovery | Prototype | AI Designer wizard (pgvector arama + tarz/bütçe); katalog gezinme akışı ayrıca düşünülmedi |
| Furniture placement | Prototype | GPT-4o yerleşim + 3D sahnede .usdz gösterim + AR görünüm |
| Design render | Prototype | Blender 4 açı + USDZ; bkz. [[3D Render Pipeline]] |
| Product detail | Prototype | ProductDetailView + "360°/AR'da Gör" |
| Seller onboarding | Defined | 2026-07-28: self-serve kayıt + admin onayı; giriş şifre veya SMS → [[2026-07-28 Mağaza kaydı self-serve + admin onayı]], [[Seller Experience]] |
| Seller product upload | Prototype (tasarım 2026-07-28'de güncellendi) | brand-panel'de çalışıyor (form + 4 açı foto → Tripo3D; güncel bakım durumu Needs Validation). Yeni tasarım: fiyat/ölçü/stok + kategoriye özel sorular + 3D zorunlu + Tripo 2 hak + admin ürün onayı + Excel toplu yükleme → [[2026-07-28 Ürün yükleme ve panel — 3D zorunlu, Tripo 2 hak]] |
| Seller Q&A (ürün soruları) | Defined | 2026-07-28: herkese açık; telefon/IBAN/link filtresi; mağazaya e-posta bildirimi → [[2026-07-28 Mağaza iletişimi — herkese açık sorular, sohbet MVP dışı]] |
| Customer–seller chat | Defined (MVP dışı) | Sipariş/checkout ile birlikte gelecek → [[2026-07-28 Mağaza iletişimi — herkese açık sorular, sohbet MVP dışı]] |
| Checkout or lead generation | Defined (v1: sepet, checkout sonra) | Güncellendi 2026-07-24: sepete ekleme MVP'de; checkout ödeme teknolojisi seçilince → [[2026-07-24 Sepet MVP'de, checkout ödeme teknolojisi seçilince]]. Checkout öncesi sepet davranışı (lead gibi mi) To Be Decided |
| Returning user flow | Not explored | |

## İlgili Notlar
- [[Roadmap]]
- [[30 Knowledge/Product/Product Flows|Product Flows (Knowledge)]]
- [[Marketplace Model]]
