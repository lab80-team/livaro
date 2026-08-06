---
type: knowledge
status: living
updated: 2026-08-06
related: []
---

# User Onboarding

## Şu An Bilinenler
- **KARARLAŞTI (2026-08-06)**: ilk ekran **giriş ekranı** — Apple / Google / telefon numarası + en altta küçük "Misafir olarak devam et". "Android ile giriş" = **Google hesabıyla giriş**; ayrı Android uygulaması yazılmayacak → [[2026-08-06 Giriş ekranı ilk ekran; misafir gezinme serbest kalır]].
- **Misafir gezinme serbest kalıyor** (22 Haz kararı, 24 Tem ve 6 Ağu teyidi): Keşfet ve ürün detayı açık. **Duvar**: "Odayı Tara", kalp ve sepete ekleme butonuna dokununca **işlem başlamadan** giriş kartı çıkar — misafir tarama emeğini kaybetmez.
- Welcome page vizyonu (2026-07-24) **rafta**: ilk ekran artık giriş ekranı → [[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu]].
- **LiDAR'sız cihaz sahibi ilk açılışta ne yaşar — CEVAPLANDI (2026-08-06)**: uygulama açılır, katalogda gezer; "Odayı Tara"ya basınca dürüst açıklama + "Haber ver" listesi + "Ürünlere göz at" görür → [[2026-08-06 MVP LiDAR'sız telefonlara açılıyor — geçici olarak haber ver listesi]].
- Bilinen engel: telefonla giriş **gerçek kullanıcıda henüz çalışmıyor** — Twilio hesabı deneme modunda, yalnız doğrulanmış numaralara SMS gidiyor. Giriş ekranı ilk ekran olduğu için pilottan önce çözülmeli.
- Kayıt: e-posta+şifre (JWT); iOS'ta kayıt olan herkes **CUSTOMER** (rol seçimi yok). Satıcılar web brand-panel'den girer. Bkz. [[2026-06-22 iOS uygulaması yalnızca müşteri tarafı]].
- Uygulama Türkçe-odaklı (CFBundleDevelopmentRegion: tr; kullanıcıya dönük hata mesajları Türkçe).
- Bunlar mühendislik varsayılanları — **bilinçli tasarlanmış bir onboarding deneyimi henüz yok** (**To Be Decided**).

## Varsayımlar
- Onboarding'in bir noktasında oda tarama/kurulum adımı olabilir — **Needs Validation** (bkz. [[Room Scanning Overview]]).

## Bilinmeyenler
- ~~Sosyal login / telefon doğrulama gerekip gerekmeyeceği~~ — **ÇÖZÜLDÜ**: üçü de var (Apple, Google, telefon SMS; 28 Tem'de kodlandı, 6 Ağu'da journey'ye yazıldı).
- ~~İlk açılış deneyimi~~ — **ÇÖZÜLDÜ (2026-08-06)**: giriş ekranı + misafir çıkışı.
- İnternetsiz açılışta giriş ekranının davranışı — **To Be Decided** → [[Open Questions]].

## Önemli Sorular
- Kullanıcı giriş yaptıktan sonra ilk hangi değeri alıyor? (Ana sayfa bugün "Odayı Tara" + "Projelerim"den ibaret; boş durumda ne göründüğü tasarlanmadı.)
- Misafirken favoriye eklediği/sepete koyduğu şey giriş yapınca hesabına taşınacak mı — **To Be Decided**.

## İlgili Notlar
- [[60 Planning/Product Flows|Product Flows]], [[Target Users]]

## Kaynaklar
- [[2026-07-08 Oturum Import — Web Temelleri ve iOS Başlangıcı]]
