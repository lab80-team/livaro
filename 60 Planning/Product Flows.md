---
type: planning
status: living
updated: 2026-07-31
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
| Seller onboarding | Implemented | 2026-07-29: `web/` (kayıt → admin onayı → giriş) + ayrı `admin/` (başvuru onay/red) build edildi, yerelde uçtan uca canlı doğrulandı. **main'e birleştirildi ve push edildi (2026-07-31, `44a4497`)**, Codex kapısı 7 turda 22 açık buldu ve hepsi kapatıldı; gerçek satıcı henüz kullanmadı (**Validated değil**) → [[2026-07-31 Kategori 3D Stratejisi, Tripo Kredi Ölçümü, iOS Doku Düzeltmesi ve Main Merge]], [[Seller Experience]] |
| Seller product upload | Implemented | 2026-07-29: yeni `web/` panelinde ürün formu (fiyat/ölçü/stok) + 4 ETİKETLİ foto (ön/arka/sol/sağ) + kategoriye göre 3D (mobilya: Tripo `multiview_to_model` v3.1, ~60 kredi/ürün; halı: Tripo'suz düz yüzey, 0 kredi; perde: tedarik yolu seçilmedi) + mağaza 3D onayı + admin ürün onayı zinciri yerelde canlı doğrulandı; eski brand-panel'e dokunulmadı (ayrı, yeni site). **main'e birleştirildi (2026-07-31)**; gerçek satıcı henüz kullanmadı (**Validated değil**); mobilyada sol/sağ eşleme gerçek 4 açıyla hâlâ doğrulanmadı → [[2026-07-29 Kategori bazlı 3D üretim stratejisi — halı düz yüzey, mobilya Tripo devam, perde sonraya]], [[Seller Experience]] |
| Seller Q&A (ürün soruları) | Defined | 2026-07-28: herkese açık; telefon/IBAN/link filtresi; mağazaya e-posta bildirimi → [[2026-07-28 Mağaza iletişimi — herkese açık sorular, sohbet MVP dışı]] |
| Customer–seller chat | Defined (MVP dışı) | Sipariş/checkout ile birlikte gelecek → [[2026-07-28 Mağaza iletişimi — herkese açık sorular, sohbet MVP dışı]] |
| Checkout or lead generation | Defined (v1: sepet, checkout sonra) | Güncellendi 2026-07-24: sepete ekleme MVP'de; checkout ödeme teknolojisi seçilince → [[2026-07-24 Sepet MVP'de, checkout ödeme teknolojisi seçilince]]. Checkout öncesi sepet davranışı (lead gibi mi) To Be Decided |
| Returning user flow | Not explored | |

## İlgili Notlar
- [[Roadmap]]
- [[30 Knowledge/Product/Product Flows|Product Flows (Knowledge)]]
- [[Marketplace Model]]
