---
type: import
date: 2026-08-04
status: processed
related: ["[[2026 08 04 Thinking Session — Admin Paneli]]"]
---

# PM Tartışması — Admin Paneli (2026-08-04)

> Kaynak: 2026-08-04 thinking session sırasında kurucu isteğiyle koşulan iki PM ajanı. PM-A merceği: marketplace operasyonu, güven & denetim. PM-B merceği: analitik, growth & veri. Önce bağımsız görüş verdiler, sonra birbirlerinin görüşüne cevap yazıp ortak v1 önerisinde buluştular. İşlendiği yer: [[2026 08 04 Thinking Session — Admin Paneli]].

## Tur 1 — PM-A (Operasyon & Güven)

### Değerlendirme

**Doğru bulduklarım:**
- İki yetkili hesap ve kayıtlara yalnız onayla izin — doğru. Asıl iş, admin hesabının seed script'ten çıkıp gerçek bir giriş sistemine kavuşması. Buna bir de "kim neyi onayladı/reddetti" kaydı (işlem günlüğü) eklenmeli; iki kişi bile olsa iz şart.
- Mağazalar sekmesi + bekleyen istek rozeti — operasyonel olarak çok mantıklı. Panelin işi kuyruk eritmek; rozet kuyruğu görünür kılar.
- Düzenlenen ürünün yeniden onaya düşmesi — güven içgüdüsü doğru, ama kapsam daraltılmalı. Stok/fiyat değişimi de onaya düşerse iki kişilik ekip boğulur; yalnız "vitrin" alanları (foto, başlık, açıklama) onaya düşsün. Not: bugün PUBLISHED üründe foto değişse 3D yenilenmiyor — foto onaya düşecekse bu tutarsızlık da çözülmeli, yoksa onaylanan foto ile 3D uyuşmaz.

**İtirazlarım:**
- **Ciro, satış, reklam sayısı:** Bu veriler yok — ödeme yok, reklam ürünü yok. Sıfır dolu kolonlar paneli kalabalıklaştırır ve "bozuk" hissi verir. Veri doğmadan alan göstermeyelim.
- **Admin ürün silme:** Kalıcı silme yerine "yayından kaldır" olmalı. Kalıcı silme mağazanın emeğini (fotolar, üretilmiş 3D) yok eder, itiraz olursa kanıt kalmaz. Silme yalnız zorunlu hallerde (yasaklı içerik gibi) ve kayıtlı olsun.
- **Kullanıcı oda taraması admin'de:** Oda taraması evin içinin verisi — KVKK açısından kişisel veri, hassas tarafa yakın. Kişi bazında "hangi odayı taramış" göstermek, kullanıcıya bunun söylenmesini (aydınlatma) ve net bir gerekçe gerektirir. Toplam tarama sayısı sorun değil; kişi-oda eşlemesi şimdilik hayır.

### Kapsam önerisi

**Şimdi yap:** Düzgün admin girişi (2 hesap) + işlem günlüğü; Mağazalar listesi (logo, isim, ürün sayısı, yayınlanmış 3D sayısı, kayıt tarihi, bekleyen istek rozeti, mağaza detayı); Ürünler listesi (durum, stok, 3D durumu + "yayından kaldır"); vitrin alanı değişince yeniden onay kuyruğu (dar kapsam); mevcut 3 ekrana basit sayaçlar.

**Veri/özellik gelince yap:** Ciro ve satış → ödeme kuruluşu seçilip checkout çalışınca. Reklam sayısı → "Sponsorlu" ürünü inşa edilince. Grafikli analitik ana sayfa → gerçek kullanıcı ve satıcı akışı başlayınca. Kişi bazlı tarama detayı → KVKK değerlendirmesi ve aydınlatma metni sonrası, muhtemelen yine toplu düzeyde.

### Kurucuya soruları

1. "2 yetkili hesap": iki ayrı kişiye ait hesap mı, ortak kullanılan tek şifre mi? Yetkileri eşit mi?
2. Rozete ne sayılacak — yalnız bekleyen ürün onayı mı; başvuru, STUCK ve düzenleme onayları da mı?
3. "Kaç mağaza giriş yapmış" derken: kayıt olan mı, onaylanan mı, son dönemde gerçekten oturum açan mı?
4. Ürün "silme"de beklenti ne: müşteri artık görmesin mi yeter, yoksa kayıt tamamen yok mu olsun? Geri alınabilir olmalı mı?
5. Ürünün hangi alanı değişince yeniden onaya düşsün? Stok ve fiyat da dahil mi?
6. Kullanıcı taramasında tam olarak ne görülmek isteniyor: sadece sayı mı, oda tipi mi, taramanın kendisi mi? Hangi kararı vermek için?
7. Analitik ana sayfaya iki kişilik ekipte kim, hangi sıklıkla, hangi karar için bakacak?

### PM-B'ye karşı tezleri

1. **Önce kuyruk, sonra grafik.** Panelin bugünkü işi operasyon. 24 Tem metrik vizyonu (görüntüleme, tıklama, tasarımda kullanım) uygulama tarafında olay toplama altyapısı ister — o ayrı bir iş paketi.
2. **Kişi bazlı davranış verisi admin'e girmesin.** Kullanıcı-oda eşlemesi KVKK riski; toplu sayılar aynı kararları verdirir.
3. **Boş kolon yok.** Ciro/reklam alanlarını "ileride lazım" diye şimdi ekrana koymak yanlış sinyal.

## Tur 1 — PM-B (Analitik & Veri)

### Değerlendirme

**Şimdi anlamlı olanlar:** Bekleyen başvuru, bekleyen ürün onayı, takılan 3D sayısı, mağaza başına ürün/yayınlanmış 3D sayısı, kayıt tarihi — boru hattından zaten doğal olarak çıkıyor.

**Boş kalacaklar:** Ciro (ödeme yok → hesaplanacak kaynak bile yok, sıfır değil "yok"), reklam sayısı (reklam ürünü inşa edilmedi), "bugün kaç kullanıcı kaydoldu / ne kadar satış" grafikleri (kullanıcı yeni, satış hiç yok).

**Boş dashboard'un maliyeti:** (a) Moral — sıfır, "ürün tutmuyor" gibi okunur ama aslında "henüz veri yok" demektir; ikisi çok farklı. (b) Alışkanlık — boş ekrana bakmayı bırakırsın, gerçek veri gelince de bakmazsın. Dashboard güveni bir kez kaybedince geri gelmez.

**Grafik mi, sayı+liste mi:** Pilotta kesinlikle sayı + isim listesi. 5 mağaza, 30 kullanıcı varken çizgi grafik gürültüdür; grafik günde yüzlerce olay olunca anlam kazanır.

**Şimdiden toplanması şart olanlar (sonradan üretilemez):** Ürün görüntüleme, tasarımda kullanılma, sepete ekleme, tarama tamamlanma — bunlar "olay" verisidir; olduğu an kaydedilmezse geçmişi asla geri getirilemez. **Ekran ertelenebilir, olay defteri ertelenemez.** Basit tek bir kayıt tablosu yeter: kim, ne yaptı, ne zaman.

### Kapsam önerisi — v1

**Şimdi yap:** Giriş sayfası = iş kuyruğu + bugünün listesi (4 sayı + son kaydolanlar listesi, grafik yok); mağaza kartları (ciro ve reklam alanını hiç koyma); ürünler sekmesi (silme yerine yayından kaldırma); görünmez iş: olay defterini kur ve yazmaya başla.

**Veri gelince yap:** Grafikler, ciro (ödeme kuruluşu seçilince), reklam sayıları, kullanıcı bazlı tarama detay ekranı (olayı şimdi topla, ekranı sonra).

### Kurucuya soruları

1. "Bugün kaç kullanıcı kaydoldu" sayısına günde kaç kez bakılacak ve bu sayı hangi kararı değiştirecek?
2. Ciro hangi kaynaktan hesaplanacak — ödeme ve sipariş kaydı yokken bu kutu ne gösterecek?
3. Tarama verisi hangi soruya cevap? "Ali hangi odayı taradı" mı lazım, yoksa "kaç tarama tasarımla bitti" mi?
4. Reklam sayısı kartı — reklam ürünü yokken şimdi mi isteniyor, ileriye not mu?
5. Ürün silme kalıcı mı? Mağazanın ~60 kredilik 3D'si ve tüm geçmişi de gider — yayından kaldırma yetmez mi?
6. Pilotun başarısını hangi TEK sayı gösterir? (Örn. mağaza başına yayına çıkan 3D'li ürün.)
7. "Kaç mağaza giriş yapmış" — giriş mi önemli, yoksa girip ürün ekleyip eklemediği mi?

### PM-A'ya karşı tezleri

1. **Erken enstrümantasyon ertelenemez.** Toplamak ucuz (tek tablo), geçmiş satın alınamaz. Pilot markalara "ürününüz şu kadar kez tasarımda kullanıldı" diyebilmek en güçlü satış kozu. Toplamak ≠ göstermek; ekranlar bekleyebilir.
2. **Giriş sayfası kalmalı ama grafik değil kuyruk olmalı.**
3. **Tarama verisi kişi takibi değil, huni ölçümü.** Tarama→tasarım→sepet zinciri MVP'nin ana hipotezini test eden tek veri; kişisiz, toplu sayım olarak tutulmalı.

## Tur 2 — Karşılıklı cevaplar

### PM-A'nın cevabı

**Taviz:** Giriş sayfası = 4 kuyruk sayısı + son kaydolanlar listesi — kabul. Olay defterinde büyük ölçüde haklı: geçmiş veri sonradan satın alınamaz; "toplamak ≠ göstermek" ayrımı itirazın büyük kısmını karşılıyor — itiraz ekran inşasınaydı, sessiz kayda değil.

**Korunan duruş:** Kişi bazlı veri admin'e girmez; olaylar kişisiz/toplu okunur; oda içeriği hiç kaydedilmez, sadece "tarama tamamlandı" sayılır. Aydınlatma metni yapılmadan kişi bazlı hiçbir görünüm açılmaz. Kuyruk işleri sıradan önce gelir.

**"Olay defteri şimdi" tezine son cevap:** Evet — ama en dar haliyle: tek tablo, 4 olay (görüntüleme, tasarımda kullanım, sepete ekleme, tarama tamamlanma), sıfır ekran, sıfır rapor. Şart: pilot-öncesi işleri (Tripo eşleme doğrulaması, katalog doldurma) masadan itmeyecek kadar küçük kalması.

### PM-B'nin cevabı

**Taviz:** İşlem günlüğü, gerçek 2 hesap, dar yeniden-onay kapsamı — katılıyorum. Kişi bazlı veri konusunda da örtüşüyoruz: admin ekranına kullanıcı-oda eşlemesi girmesin; KVKK itirazı yerinde.

**Korunan duruş — olay defteri şimdi:** Ekran yok, rapor yok, sadece kayıt. 4 olay tipi, tek tablo, uygulamada 4 noktaya birer satır kayıt çağrısı — panel ekranı yapmaktan çok daha küçük iş. Pilot BAŞLAMADAN kayıt açık olmazsa ilk haftaların verisi sonsuza dek yok. Tripo doğrulamasını geciktirmez; paralel, küçük, geri-alınamaz-fırsat işi.

**Küçük ek:** Onay kayıtlarında **red nedeni** de tutulsun — ileride "mağazalar en çok neden takılıyor" sorusunun tek veri kaynağı bu olur; sonradan eklenirse geçmiş kaybolur.

## İkisinin imzaladığı ortak v1 önerisi

1. Gerçek 2 admin hesabı + kim-neyi-onayladı günlüğü (red nedeniyle).
2. Giriş sayfası = iş kuyruğu: 4 bekleyen sayısı + son kayıtlar listesi; grafik yok.
3. Mağaza kartları: logo, isim, ürün/3D sayısı, rozet, kayıt tarihi; ciro-reklam alanı yok.
4. Ürünler sekmesi: liste + durum; silme değil yayından kaldırma (kalıcı silme yalnız yasaklı içerik, kayıtlı).
5. Dar yeniden-onay: yalnız vitrin alanları; foto-3D tutarsızlığı çözülerek.
6. Görünmez iş: 4 olaylık kayıt defteri açılır; ekranı v2'ye.

> **Not:** Kurucu, kararlarını bu tartışmanın ÜSTÜNE verdi — birkaç noktada PM önerisinden ayrıştı (kişi bazlı kullanıcı kartı + RoomPlan çıktısı; panelden yetkili ekleme). Nihai kararlar: [[2026 08 04 Thinking Session — Admin Paneli]].
