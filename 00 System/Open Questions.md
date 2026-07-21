---
type: system
status: living
updated: 2026-07-21
---

# Open Questions

> Çözülmemiş sorular. **Kanıt veya ekip kararı olmadan yanıtlanmaz.** Yanıt netleşince ilgili bilgi/karar notuna taşınır ve buradan kaldırılır (veya "çözüldü" işaretlenip linklenir).
>
> ⭐ = [[2026-07-21 PM Panel Tartışması]]'nın kuruculara yönelttiği öncelikli sorular.
> Kurucu yanıtları (2026-07-21): **İlk ürün kapsamı KARARLAŞTI** → [[2026-07-21 İlk ürün kapsamı görselleştirme + lead]] (checkout ileride). LiDAR ve hedef-an soruları açık; satıcı tarafında **aday var, henüz görüşülmedi**.

## Ürün (Product)
- ~~İlk ürün ne olmalı?~~ **ÇÖZÜLDÜ (2026-07-21)**: görselleştirme + lead katmanı; checkout ileride → [[2026-07-21 İlk ürün kapsamı görselleştirme + lead]]. Türev sorular açık: MVP'nin tam özellik listesi ve lead aksiyonunun tanımı (buton? form? satıcıya yönlendirme?) — **To Be Decided**.
- ⭐ Hedef kullanıcı kim ve hangi anda devreye giriyoruz (taşınma / tadilat / tek parça alım)? Akış toleransı, kanal ve katalog kapsamı bu cevaba bağlı.
- ⭐ İlk 30 kullanıcı hangi kanaldan gelecek? (Kanal hipotezi olmayan MVP test edilemez.)
- Hangi akışlar basit kalmalı, hangileri gelişmiş işlevsellik gerektiriyor? (6 adımlık tarama akışının terk oranı ölçülmedi.)
- Bkz. [[Product Overview]], [[60 Planning/Product Flows|Product Flows]]

## Pazaryeri / İş Modeli
- ~~Checkout mu lead mi?~~ **İlk sürüm için ÇÖZÜLDÜ (2026-07-21)**: lead; sepet+checkout ileride gelecek (zamanlama TBD) → [[2026-07-21 İlk ürün kapsamı görselleştirme + lead]]. Açık kalan: gelir modeli detayı (komisyon / lead ücreti / abonelik) ve checkout'un ne zaman geleceği.
- Checkout geldiğinde ödeme sağlayıcısı ne olacak (Iyzico mı, başka mı)? Kurucu bunun **henüz belirsiz** olduğunu açıkça belirtti (2026-07-21) — Haziran'daki Iyzico planı bir olasılık, karar değil.
- ⭐ Render + Tripo3D + OpenAI kullanım başına maliyet ne; kullanıcı/satıcı başına kaç render/model öngörülüyor? (Birim ekonomisi hiç hesaplanmadı.)
- ⭐ İlk gerçek satıcı kim olacak; bugüne kadar bir mobilya satıcısıyla konuşuldu mu? Katalog neden yeniden doldurulmadı?
- Bkz. [[Marketplace Model]], [[Seller Experience]]

## Oda Tarama / 3D
- ⭐ LiDAR'lı iPhone zorunluluğu bilinçli bir "premium segment" seçimi mi, geçici teknik kısıt mı? (LiDAR'sız fallback yatırım kararını belirler.)
- ARKit mesh (ısınma nedeniyle kapalı) tarama-sonrası işlemeyle geri açılabilir mi? (PM'lerin ortak sırası: önce funnel ölçümü, sonra ucuz deneyler, ARKit en son.)
- RoomPlan yanlış algıları (TV=pencere) için kullanıcıya düzeltme aracı gerekir mi?
- Kabul edilebilir minimum kalite çıtası ne? ("Odamı tanıdım / bu görselle satın alırdım" — dış kullanıcı verisi sıfır.)
- Bkz. [[Room Scanning Overview]], [[3D Render Pipeline]]

## Veri / Gizlilik (yeni — PM panelinin ortak tespiti)
- ⭐ KVKK: ev içi tarama + fotoğraflar yurt dışı işleyicilere (OpenAI, Modal, Replicate) gidiyor — açık rıza, aydınlatma metni, saklama süresi planı var mı? Dış teste çıkmadan asgari rıza + saklama politikası şart.

## Mühendislik
- ⭐ TestFlight ve production deployment'ın önündeki somut engel ne, ne kadarlık iş? (Dış kullanıcıya ulaşmanın tek yolu; bkz. [[Deployment Strategy]].)
- Texture regresyonlarına karşı otomatik doğrulama (golden-image, R2 çıktı kontrolü) kurulacak mı?
- 2-3 dk'lık async render başarısız olduğunda kullanıcı ne görüyor? (Hata UX'i tanımsız.)
- Eski gpt-image-1 render yolunun akıbeti; `coverageGateEnabled` bayrağı.
- brand-panel'in güncel bakım durumu (Temmuz'da hiç dokunulmadı) — çalışıyor mu?
- Bkz. [[System Architecture]], [[Known Pitfalls]]

## Test (Testing)
- İlk otomasyon nereye: texture üretim zinciri mi, tarama→kayıt API'si mi? Bkz. [[E2E Testing Strategy]]

## Müşteri Deneyimi
- Bilinçli tasarlanmış onboarding yok — ilk açılışta kullanıcı ne görmeli, ilk değeri nasıl almalı? Bkz. [[User Onboarding]]
- LiDAR'sız cihaz sahibi ilk açılışta ne yaşar?

## Kayıt
- Çözülenler buradan karar/bilgi notlarına taşınır; geçmiş için Git. Kaynak: [[2026-07-21 PM Panel Tartışması]], [[2026-07-19 Proje Kurulum Brief]].
