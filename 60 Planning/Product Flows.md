---
type: planning
status: living
updated: 2026-08-06
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
| User registration | Prototype | Apple + Google + telefon SMS girişi cihazda çalışıyor (28 Tem). **Journey 6 Ağu'da tanımlandı**: giriş ekranı ilk ekran + misafir çıkışı → [[2026-08-06 Giriş ekranı ilk ekran; misafir gezinme serbest kalır]]. Bekleyen: Twilio deneme modundan çıkarılmalı |
| User onboarding | Defined | 6 Ağu: giriş → ana sayfa → Odayı Tara/Projelerim. Bkz. [[User Onboarding]] |
| Room creation | Prototype | "Projelerim" + oda detay ekranları mevcut; 6 Ağu'da tek buton "Kaydet ve Odayı Tasarla" kararı → [[2026-08-06 Tarama akışı — ölçü doğrulama ekranı ve tek buton]] |
| Room scanning | Prototype | RoomPlan + 4-8 köşe foto (+ planda yakın çekimler) — 6 Ağu'da **fotoğraf adımları korundu**; ardına mobilyasız **ölçü doğrulama ekranı** eklenecek; bkz. [[Room Scanning Overview]] |
| Manual room setup | Not explored | LiDAR'sız cihaz artık hedefte ama teknoloji seçilmedi; MVP'de "Haber ver" listesi → [[2026-08-06 MVP LiDAR'sız telefonlara açılıyor — geçici olarak haber ver listesi]] |
| Furniture discovery | Defined | AI Designer wizard (pgvector + tarz/bütçe) prototipte. **Keşfet akışı 6 Ağu'da karara bağlandı**: kategoriler + ürün ızgarası, MVP'de yalnız "Sırala" → [[2026-08-06 Keşfet ve Profil ekran kapsamı]] |
| Furniture placement | Prototype | GPT-4o yerleşim + 3D sahnede .usdz gösterim + AR görünüm. Yerleşim kalitesi hâlâ **test edilmedi** |
| Design render | Defined | Blender 4 açı + USDZ; 6 Ağu'da sonuç ekranı ve bekleme deneyimi tanımlandı; güzelleştirme katmanı kapatılıyor → [[2026-08-06 Tasarım sonuç ekranı — döner Blender modeli, fotogerçekçi render arkada]], [[2026-08-06 Render güzelleştirme katmanı kapatılır — saf Blender çıktısı]] |
| Product detail | Prototype | ProductDetailView + "360°/AR'da Gör" + favori kalbi. **Varyant MVP'de yok** (6 Ağu'da konuşuldu, karara bağlanıp aynı gün geri alındı) → [[2026-08-06 Ürün varyantı MVP dışı — ileride eklenecek]] |
| Favorites | Defined (yapılmadı) | 6 Ağu: **favorileme Keşfet ürün kartı + ürün detayındaki kalpten**; yalnız ürünler; "Odalar" ileride, sekme çubuğu MVP'de yok. **Ekran boş yer tutucu, veritabanında tablo yok** → [[2026-08-06 Favorileme Keşfet üzerinden — Sepet ekranı MVP'de yapılır]], [[2026-08-06 Favorilerde Odalar sekmesi ileride — MVP'de sekme çubuğu yok]] |
| Profile | Defined (yapılmadı) | 6 Ağu: görseldeki tam liste; Siparişlerim/Adreslerim/Ödeme Yöntemleri "Yakında" ekranıyla → [[2026-08-06 Keşfet ve Profil ekran kapsamı]] |
| Seller onboarding | Implemented | 2026-07-29: `web/` (kayıt → admin onayı → giriş) + ayrı `admin/` (başvuru onay/red) build edildi, yerelde uçtan uca canlı doğrulandı. **main'e birleştirildi ve push edildi (2026-07-31, `44a4497`)**, Codex kapısı 7 turda 22 açık buldu ve hepsi kapatıldı; gerçek satıcı henüz kullanmadı (**Validated değil**) → [[2026-07-31 Kategori 3D Stratejisi, Tripo Kredi Ölçümü, iOS Doku Düzeltmesi ve Main Merge]], [[Seller Experience]] |
| Seller product upload | Implemented | 2026-07-29: yeni `web/` panelinde ürün formu (fiyat/ölçü/stok) + 4 ETİKETLİ foto (ön/arka/sol/sağ) + kategoriye göre 3D (mobilya: Tripo `multiview_to_model` v3.1, ~60 kredi/ürün; halı: Tripo'suz düz yüzey, 0 kredi; perde: tedarik yolu seçilmedi) + mağaza 3D onayı + admin ürün onayı zinciri yerelde canlı doğrulandı; eski brand-panel'e dokunulmadı (ayrı, yeni site). **main'e birleştirildi (2026-07-31)**; gerçek satıcı henüz kullanmadı (**Validated değil**); mobilyada sol/sağ eşleme gerçek 4 açıyla hâlâ doğrulanmadı → [[2026-07-29 Kategori bazlı 3D üretim stratejisi — halı düz yüzey, mobilya Tripo devam, perde sonraya]], [[Seller Experience]] |
| Seller Q&A (ürün soruları) | Defined | 2026-07-28: herkese açık; telefon/IBAN/link filtresi; mağazaya e-posta bildirimi → [[2026-07-28 Mağaza iletişimi — herkese açık sorular, sohbet MVP dışı]] |
| Customer–seller chat | Defined (MVP dışı) | Sipariş/checkout ile birlikte gelecek → [[2026-07-28 Mağaza iletişimi — herkese açık sorular, sohbet MVP dışı]] |
| Checkout or lead generation | Defined (v1: sepet, checkout sonra) | Güncellendi 2026-07-24: sepete ekleme MVP'de; checkout ödeme teknolojisi seçilince → [[2026-07-24 Sepet MVP'de, checkout ödeme teknolojisi seçilince]]. **Netleşti 2026-08-06**: **sepet ekranı MVP'de yapılacak, arkasındaki sistem aşama aşama doldurulacak**; "Siparişi Onayla" butonu konmayacak, yerinde dürüst bilgi satırı; sepet pasif liste, mağazaya talep iletilmez → [[2026-08-06 Sepette ödeme butonu yok — dürüst bilgi satırı]], [[2026-08-06 Favorileme Keşfet üzerinden — Sepet ekranı MVP'de yapılır]]. **Sepet bugün özellik olarak yok** (veritabanında tablo bile yok) |
| Returning user flow | Not explored | |

## İlgili Notlar
- [[Roadmap]]
- [[30 Knowledge/Product/Product Flows|Product Flows (Knowledge)]] — MVP uygulama akışının ekran ekran son hâli orada
- [[2026 08 06 Thinking Session — Uygulama User Journey]]
- [[Marketplace Model]]
