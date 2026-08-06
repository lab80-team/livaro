---
type: knowledge
status: living
updated: 2026-08-06
aliases: ["Product Flows (Knowledge)"]
related: []
---

# Product Flows (Knowledge)

> Bu not, akışlar hakkında **bilinenleri** tutar. Akışların **tasarım durumu** (Not explored → Validated) için bkz. [[60 Planning/Product Flows|Product Flows (Planning)]].

## Şu An Bilinenler
- Tasarlanması gereken akışların bir listesi var (bkz. planlama notu).
- Prototipte çalışan akışlar var (tarama, AI tasarım, render — durumlar planlama notundaki tabloda "Prototype") ama hiçbir akış dış kullanıcıyla **Validated** değil.
- Tarama akışının güncel adımları: oda tara → 4-8 köşe foto → (isteğe bağlı, yeni) zemin + duvar yakın çekim → kayıt/analiz. Bkz. [[Room Scanning Overview]].
- **AI Designer wizard** (25 Haz'dan beri): 4 adım — (1) serbest metin ("Hayalinizdeki mekanı anlatın…"), (2) tarz seçimi (6 kart: Modern Lüks, Skandinav, Minimalist, Japandi, Klasik Şık, Boho), (3) renk paleti, (4) bütçe min/max ₺ → "AI ile Tasarla ✨". Sonuç: designConcept metni + 3D sahne (gerçek .usdz'lerle) + ürün kartları (designReason'lı) + "AR ile Odanda Gör" (otomatik yerleşim — kullanıcı elle yerleştirmez) + "Yeniden Tasarla". Tasarımlar `DesignResult` olarak kaydedilir; Projelerim'den geri dönülebilir.
- Ana navigasyon: 5 sekme (Ana Sayfa, Keşfet, Favoriler, Sepet, Profil); tarama Ana Sayfa'daki "Odayı Tara" CTA'sından. Bkz. [[2026-06-24 iOS tasarım sistemi LivaroTheme]].
- **Thinking session teyit ve eklemeleri (2026-07-24)**:
  - Wizard akışı **korunuyor** (serbest metin → tarz → renk → bütçe); anlatımdaki "önce bütçe, en son chat" sırası benimsenmedi. **Tarz kartlarına fotoğraf eklenecek**; karşılıklı konuşan **chat ileriki sürümde**.
  - Onay adımı: kullanıcı istediklerini anlattıktan sonra AI **özet sunar ve onay ister**; onay sonrası tasarım üretilir.
  - Tasarım sonucu otomatik çıkar (kullanıcı ayrıca render butonuna basmaz); yanında gerçekçi **2D fotoğraflar**.
  - MVP: hem boş oda hem dolu oda (AI boşaltır) taranır, sıfırdan tasarlanır; ürün çıkarma (yeri boş kalır); **alternatifle değiştirme MVP'de YOK, sonra** (teyit turu — çelişki çözüldü); **AR tüm oda, MVP'de**; **yeniden tasarla 2 hak**, toplam tasarım sayısında kısa vadede sınır yok → [[2026-07-24 MVP tasarım kapsamı — oda boşaltılır, sıfırdan tasarım]].
  - **KARAR (teyit turu)**: anlık deneyim — canlı 3D sahnede anında değişiklik; fotogerçekçi render arka planda bildirimle; tek ürün değişimi tam render tetiklemez → [[2026-07-24 Anlık deneyim — canlı 3D sahne, render arka planda]].
  - Welcome page vizyonu: güzel ev tasarımı arka planı + "Odayı tara" / "Projelerim" seçenekleri (tasarlanmadı). **Rafta — 6 Ağu'da ilk ekran giriş sayfası oldu.**
  - Kaynak: [[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu]].

## MVP Uygulama Akışı — son hâl (2026-08-06 thinking session)

> Kaynak: [[2026 08 06 Thinking Session — Uygulama User Journey]]. 24 Temmuz'la farkların tablosu o notun sonunda.

**Ekran ekran akış:**
1. **Giriş ekranı** (ilk ekran): Apple / Google / telefon numarası + en altta küçük "Misafir olarak devam et". "Android ile giriş" = Google hesabıyla giriş; ayrı Android uygulaması yok. → [[2026-08-06 Giriş ekranı ilk ekran; misafir gezinme serbest kalır]]
2. **Ana Sayfa**: "Odayı Tara" + "Projelerim" sabit; alt sekmeler Ana Sayfa / Keşfet / Favoriler / Sepet / Profil.
3. **Odayı Tara**: LiDAR'lı iPhone'da RoomPlan; LiDAR'sız telefonda dürüst açıklama + "Haber ver" + "Ürünlere göz at". → [[2026-08-06 MVP LiDAR'sız telefonlara açılıyor — geçici olarak haber ver listesi]]
4. **Köşe fotoğrafları + zemin/duvar yakın çekimi** (kalıyor — odanın gerçek dokusunun kaynağı).
5. **Ölçü doğrulama ekranı**: mobilyasız görünüm + "taslak görünüm" notu + "Ölçüler doğru, devam et" / "Yeniden tara". Bir daha gösterilmez. → [[2026-08-06 Tarama akışı — ölçü doğrulama ekranı ve tek buton]]
6. **Tek buton "Kaydet ve Odayı Tasarla"** → oda ismi → doğrudan tasarım.
7. **4 soru** (serbest metin → tarz → renk → bütçe) + AI özet sunar, onay ister (24 Tem kararı korunuyor).
8. **Bekleme arka planda sürer**: adım listesi (yüzde yok) + "Arka planda devam et" + sekme üstü şerit; bitince yeşil "hazır". Bildirim MVP'de yok. → [[2026-08-06 Tasarım beklemesi arka planda sürer — üst şerit haber verir]]
9. **Tasarım sonuç ekranı**: "Kat Planı | 3D" seçici → büyük **döndürülebilir Blender modeli** → kısa not (sans-serif 13pt, en fazla 2 satır, "Detay" bağlantısı) → ürün kutucukları → alt sabit "AR ile Odanda Gör" + "Yeniden Tasarla". Fotogerçekçi render arkada üretilir, hazır olunca aynı ekranda şeritle sunulur. "Kat Planı" = **mobilyalı** yerleşim planı. → [[2026-08-06 Tasarım sonuç ekranı — döner Blender modeli, fotogerçekçi render arkada]]
10. **Sepet**: ekran MVP'de yapılır (arkasındaki sistem aşama aşama doldurulur); tek tek veya "Tümünü Ekle"; **adet var, varyant yok**; ödeme butonu yok, yerinde dürüst bilgi satırı. → [[2026-08-06 Sepette ödeme butonu yok — dürüst bilgi satırı]], [[2026-08-06 Favorileme Keşfet üzerinden — Sepet ekranı MVP'de yapılır]], [[2026-08-06 Ürün varyantı MVP dışı — ileride eklenecek]]
11. **Keşfet**: kategoriler + 2 sütun ürün ızgarası; MVP'de yalnız "Sırala". **Favorileme buradan yapılır** (ürün kartındaki + ürün detayındaki kalp). **Profil**: görseldeki tam liste, olmayan satırlar "Yakında" ekranıyla. **Favoriler**: yalnız ürünler, sekme çubuğu yok. → [[2026-08-06 Keşfet ve Profil ekran kapsamı]], [[2026-08-06 Favorileme Keşfet üzerinden — Sepet ekranı MVP'de yapılır]], [[2026-08-06 Favorilerde Odalar sekmesi ileride — MVP'de sekme çubuğu yok]]

**Kural olarak yazılanlar:** "Yeniden tasarla" hakkı yalnız kullanıcı isteğinde yanar ([[2026-08-06 Yeniden tasarla hakkı yalnız kullanıcı isteğinde yanar]]); render güzelleştirme katmanı kapatılır ([[2026-08-06 Render güzelleştirme katmanı kapatılır — saf Blender çıktısı]]).

**Bu akışın en büyük gizli maliyeti:** Favoriler ve Sepet bugün **ekran değil, özellik olarak yok** — veritabanında tabloları bile yok. Kurucu ikisinin de MVP'de yapılmasını, arkasındaki sistemin aşama aşama doldurulmasını seçti.

**Varyant (renk/kumaş/ölçü seçeneği) MVP'de yok** — oturumda önce "tam varyant, pilot öncesi" denildi, sonuçları (mağaza panelinin yeniden yazılması + katalog 3D maliyetinin çarpılması) görülünce aynı oturumda geri alındı. Ürün = tek fiyat + tek ölçü + tek 3D model → [[2026-08-06 Ürün varyantı MVP dışı — ileride eklenecek]].

**Yöneticilerin ayırdığı iki kavram karışıklığı:** (1) "Tasarımı Blender üzerinde yapsın" — Blender tasarım ortamı değil, görüntü alma aracı; yerleşimi GPT-4o RoomPlan geometrisi üzerinde yapıyor, Blender sahnesi aynı veriden kuruluyor. (2) "Fotogerçekçi ama canlı 3D gibi" — fotogerçekçi görüntü döndürülemeyen bir fotoğraftır; karar bu gerilimi bölerek çözdü.

## Varsayımlar
- Bazı akışlar basit, bazıları (özellikle oda tarama ve mobilya yerleştirme) gelişmiş olacak — **Needs Validation**.

## Bilinmeyenler
- Her akışın nihai adımları — **To Be Decided**.

## Önemli Sorular
- Hangi akışlar MVP'de zorunlu?

## İlgili Notlar
- [[60 Planning/Product Flows|Product Flows (Planning)]]
- [[User Onboarding]]
- [[Room Scanning Overview]]

## Kaynaklar
- [[Meeting Index]]
