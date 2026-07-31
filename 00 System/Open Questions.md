---
type: system
status: living
updated: 2026-07-31
---

# Open Questions

> Çözülmemiş sorular. **Kanıt veya ekip kararı olmadan yanıtlanmaz.** Yanıt netleşince ilgili bilgi/karar notuna taşınır ve buradan kaldırılır (veya "çözüldü" işaretlenip linklenir).
>
> ⭐ = PM incelemelerinin öncelikli işaretledikleri ([[2026-07-21 PM Panel Tartışması]], [[2026-07-24 PM Gözden Geçirme — Thinking Session]]).
> 2026-07-24 thinking session'da çok sayıda soru çözüldü → [[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu]] ve yeni kararlar: [[Decision Index]].

## Teyit turu sonuçları (2026-07-24 — hepsi çözüldü)
- ~~Alternatifle değiştirme MVP'de mi?~~ **ÇÖZÜLDÜ**: MVP'de yok, sonra gelecek.
- ~~Checkout gelene kadar sepet?~~ **ÇÖZÜLDÜ**: şu anlık **pasif liste** (mağazaya talep iletilmez).
- ~~Anlık + gerçekçi görüntü stratejisi?~~ **ÇÖZÜLDÜ**: öneri kabul edildi → [[2026-07-24 Anlık deneyim — canlı 3D sahne, render arka planda]].
- ~~Emanet modeli?~~ **ÇÖZÜLDÜ**: lisanslı ödeme kuruluşuyla → [[2026-07-24 Emanet lisanslı ödeme kuruluşuyla]].
- Ayrıca: iptal/iade **yasaya uygun** tasarlanacak (detay hâlâ açık, aşağıda); bütçe aşım tavanı **%20**; hizmet bedeli baştan alınacak (kurucu kararı); birim maliyet analizi bilinçli olarak MVP sonrasına bırakıldı; GPT-4o testi MVP altyapısı bitince.

## PM 2. tur önerileri — kurucu cevapları (2026-07-24, Bölüm 4)
- ~~Harcama tavanı/limit anahtarı~~ — **RET**: şimdilik gerek yok; birim maliyet analizini kurucular kendileri yapıp paylaşacak → [[2026-07-24 PM önerileri kararları — bulut taşınma, kalite çıtası, bütçe rozeti]].
- ~~Buluta taşınma öne çekilsin mi?~~ — **KABUL**: backend buluta taşınacak (aynı karar notu).
- ~~Dolu oda/AR kalite çıtası~~ — **KABUL**: iç kontrol noktası; tutmazsa "deneysel" etiketiyle açılır (aynı karar notu).
- ~~Bütçe aşımı rozeti~~ — **KABUL**: aşan ürünlere "bütçenin %X üstünde" rozeti (aynı karar notu).
- Hâlâ açık (öneri statüsünde): render sürerken değişiklik yapılırsa görsel sürüm/etiket kuralı; hizmet bedelinin iade koşulları + tahsilat yolu; tek sayfalık iade akışı; bot/kötüye kullanım koruması; GPT-4o "iyi yerleşim" ölçütü + ucuz ön deneme (test detayları — gün sayısı, tarama sayısı, prompt kullanımı — **To Be Decided**).

## Ürün (Product)
- ~~İlk ürün ne olmalı?~~ **ÇÖZÜLDÜ** (2026-07-21 + 2026-07-24): görselleştirme + sepet; checkout ödeme teknolojisi seçilince → [[2026-07-24 Sepet MVP'de, checkout ödeme teknolojisi seçilince]].
- ~~MVP tasarım kapsamı?~~ **ÇÖZÜLDÜ (2026-07-24)**: dolu oda boşaltılır, sıfırdan tasarım; ürün çıkarma var; AR tüm oda; yeniden tasarla 2 hak → [[2026-07-24 MVP tasarım kapsamı — oda boşaltılır, sıfırdan tasarım]].
- ⭐ İlk 30 kullanıcı hangi kanaldan gelecek? Kurucu beyanı (2026-07-24): ilk test kendi çevrede; **B2C go-to-market belli değil**.
- Hangi akışlar basit kalmalı? (6 adımlık tarama akışının terk oranı ölçülmedi.)
- Bütçe aşıldığında kullanıcıya ne gösterilecek? (Tavan %20'ye güncellendi → [[2026-07-24 Bütçe aşım tavanı yüzde 10]]; PM önerisi: "bütçenin %X üstünde" rozeti + kullanıcıya sorma.)
- "Dolu odayı dijital boşaltma" teknik olarak nasıl yapılacak? (PM alternatifi: MVP'de "boş odanı tara" demek.)
- Teslimat tarihi tercihi akışın neresinde sorulacak (tasarımdan önce mi sonra mı)?
- İnterneti olmayan ama oturumu olan kullanıcı, uygulama açılışında giriş sayfasını (login gate) görmeli mi? Şu anki davranış (2026-07-28, ilk açılış giriş kapısı işinin kod incelemesinde çıktı): oturum silinmez ama o açılışta giriş sayfası görünür; internet gelince sonraki açılışta oturum kendiliğinden tanınır. Offline'da farklı bir ekran (ör. "bağlantı yok") gösterilmeli mi — **To Be Decided**.
- Bkz. [[Product Overview]], [[60 Planning/Product Flows|Product Flows]]

## Pazaryeri / İş Modeli
- ⭐ **Ödeme sağlayıcısı hangisi olacak?** (Iyzico Pazaryeri/PayTR/Craftgate vb. adaylar; hiçbiri seçilmedi.) Emanet modeli kararlaştı (lisanslı kuruluş → [[2026-07-24 Emanet lisanslı ödeme kuruluşuyla]]); seçim, emanet/ödeme planı özelliklerine göre yapılacak. Hizmet bedelinin tahsilat yolu da buna bağlı.
- ⭐ **İptal/iade "yasaya uygun" nasıl tanımlanacak?** (Yön kararlaştı; detay belli değil.) 14 gün cayma + özel üretim istisnası + iade kargosunu kim öder + para kaç günde döner + emanetin satıcıya geçiş anı. (PM önerisi: e-ticaret avukatından pilot paketi; ilk satıştan önce tek sayfalık iade akışı.)
- ⭐ Render + Tripo3D + OpenAI kullanım başına maliyet ne? **Kurucu kararı (teyit turu): tam analiz MVP hazır olunca** (teknoloji seçimleri netleşince). Ara önlem soruları (harcama tavanı, tasarım başına maliyet kaydı) yukarıda.
- Avans oranı ne olacak? (Mağazalarla konuşulup belirlenecek.) Gecikme cezasının oranı/meblağı?
- Defo anlaşmazlığında hakemlik: 48 saat itiraz penceresi var; mağaza kabul etmezse son kararı kim verir? Emanetteki para hangi kuralla serbest bırakılır? Geri taşıma masrafı kimde?
- Çok markalı sepette bir marka teslim tarihine yetişemezse süreç ne? Montaj/kurulum kimin sorumluluğu?
- Chat'te karşılıklı onayın kaydı (fiyat/ölçü/tarih tek yerde) nasıl tutulacak? Platform dışına kaçış (telefon yasağını AI denetleyecek) yeterli mi?
- Showroom kaçağı: kullanıcının mağazadan alımı nasıl takip edilecek (indirim kodu/referans)? Reklam geliri bunu gerçekten telafi eder mi?
- ~~Hizmet bedelli indirim modeli yaşayacak mı?~~ **Kurucu kararı (teyit turu)**: hizmet bedeli **baştan alınacak** (uzun vade modeli). Açık kalan: bedelin iade koşulları, tutar, tahsilat yolu, mağaza gecikirse ne olacağı.
- Reklamın tasarım algoritmasına gömülmesi (kurucu planı) ↔ tasarım tarafsızlığı (PM itirazı) — nihai kural ne?
- ⭐ İlk satıcı görüşmesi ne zaman? (Karar: MVP bitince. PM önerisi: MVP bitmeden 5-10 firmayla ön görüşme + 1 sayfalık pilot teklifi.) Pilot kategori listesi (kaç kategori × 2 firma) netleşmedi.
- **Mağaza paneli journey'sinden kalan açıklar (2026-07-28)** → [[2026 07 28 Thinking Session — Mağaza Web Paneli User Journey]]:
  - Mağaza başvurularının **onay/red kriterleri** ne olacak; red gerekçesi mağazaya söylenecek mi? (Self-serve kayıt kaldığı için kapının tek filtresi bu — PM uyarısı.) **Not (2026-07-29 build):** mevcut kod red gerekçesini (`rejectionNote`) mağazaya GÖSTERMİYOR (iç kayıt) — bu, build'in kendi spec'inin bir varsayımıydı, kurucu kararı değil; soru resmen hâlâ açık.
  - Tripo3D için **aylık bütçe/harcama tavanı** var mı? (2 deneme hakkı var ama toplam maliyet tavanı yok.)
  - Herkese açık ürün sorularında **denetim kuralı**: hakaret/spam/yanlış bilgiye kim, hangi sıklıkla bakacak? (Telefon/IBAN/link filtresi kararlaştı; içerik denetimi açık.)
  - **KVKK aydınlatma + satıcı sözleşmesi metinlerini** kim/nasıl hazırlayacak (avukat?) — kayıtta iki onay kutusu kararlaştı. **Güncelleme (2026-07-29 build):** `/kvkk` ve `/satici-sozlesmesi` yer tutucu sayfaları artık var ve kayıt formundan linkleniyor, ama içerik hâlâ "TASLAK — hukuki metin değildir, avukat onayı beklenmektedir" şeridiyle işaretli — gerçek hukuki metin hâlâ yok.
  - **Kategori listesi + kategoriye özel soru setleri** hazır değil; ayrı bir thinking session planlandı, ekip önceden hazırlanacak (görev: [[Task Board]]). Ürün formu ve Excel şablonu buna bağımlı. **Güncelleme (2026-07-29 build):** geçici liste (mobilya/halı/perde) artık ürün formunun canlı kategori kaynağı; Excel toplu yükleme hâlâ yapılmadı, bu listeye bağımlılığı devam ediyor.
- **Mağaza web + yönetim sitesi build'inden kalan açıklar (2026-07-29)** → [[2026-07-29 Build Oturumu — Mağaza Web ve Yönetim Sitesi]]:
  - ~~**R2 bucket'ta CORS politikası yok** → 3D model tarayıcıda yüklenmiyor~~ — **ÇÖZÜLDÜ (2026-07-29 akşamı)**: kurucu Cloudflare panelinden bucket'a CORS politikasını ekledi. Doğrulandı: presigned GLB tarayıcıdan 200 OK ile indi (11,8 MB), `<model-viewer>` modeli render etti ve sürükleyince döndü. Kodda değişiklik gerekmedi; kabul turu böylece 8/8 tamamlandı.
  - **Gerçek multi-view Tripo denemesi KOŞULDU (2026-07-29 akşamı, kurucu onayıyla, kredi harcandı) — kısmen çözüldü:**
    - ✅ **Boru hattı gerçek Tripo'da uçtan uca çalışıyor**: bir Hereke halısıyla (4 fotoğraf gerçek etiketli uçtan yüklendi, `TRIPO3D_FAKE=0`) `multiview_to_model` isteği kabul edildi, model üretildi (`tripoTaskId` alındı, `status=COMPLETED`, hata yok), indirilip ölçeklendi, R2'ye yazıldı, panelde döndürülerek incelendi. Çıkan model orijinal halının kendisiydi (bordo zemin, krem bordür, çiçek deseni).
    - ❌ **Hâlâ açık: ön/arka/sol/sağ → front/left/back/right eşlemesi doğru mu (model aynalanıyor mu)?** Bu denemede ölçülemedi: halının 4 fotoğrafı gerçek 4 açı değil (biri düz üstten katalog çekimi, biri zeminde açılı çekim) ve halı düz bir ürün olduğu için yan açı kavramı zaten anlamsız. Eşlemeyi doğrulamak için **bir mobilyanın gerçek ön/arka/sol/sağ çekimleri** gerekiyor — pilottan önce yapılmalı.
    - ⚠️ Yan bulgu: katalogdaki mevcut `k` ürününün "4 fotoğrafından" ikisi **birebir aynı dosya** (md5 eşit) — yani gerçek 4 açı değil. Pilot öncesi mevcut katalog fotoğraflarının gerçekten 4 farklı açı olup olmadığı gözden geçirilmeli.
  - E-posta gönderimi hâlâ dev-only log taşıyıcı; gerçek sağlayıcı seçilmedi.
  - **"Şifremi unuttum" akışı yok.**
  - `users.phone`'da DB seviyesinde `@unique` kısıtı yok — iki hesap aynı telefon numarasıyla yarışarak kayıt olabilir (e-posta yolu P2002 ile korunuyor, telefon değil).
  - SMS girişinde `signInWithOtp` Supabase'in varsayılanı `shouldCreateUser: true` ile çağrılıyor — gerçek Supabase kimlik bilgileri yapılandırılınca herkes rastgele bir telefon numarasına gerçek SMS gönderilmesini tetikleyebilir (maliyet/kötüye kullanım riski; hesap ele geçirme değil, çünkü backend hâlâ eşleşen SELLER/ADMIN telefonu arıyor). Şu an `.env` boş olduğu için SMS sekmesi hiç görünmüyor, risk aktif değil.
- **Kategori 3D stratejisi + main merge turundan kalan açıklar (2026-07-29 – 31)** → [[2026-07-31 Kategori 3D Stratejisi, Tripo Kredi Ölçümü, iOS Doku Düzeltmesi ve Main Merge]]:
  - **Perde tedarik yolu seçilmedi** — hazır kıvrımlı model kütüphanesi hangi yoldan edinilecek (freelancer $500-1500/3-5 hafta mı, hazır asset mi)? Lisansların "kumaş değiştirilebilir UV" desteği satın almadan bilinmiyor — asıl risk → [[2026-07-29 Kategori bazlı 3D üretim stratejisi — halı düz yüzey, mobilya Tripo devam, perde sonraya]].
  - **Mobilyada Tripo'nun ön/arka/sol/sağ → front/left/back/right eşlemesi hâlâ doğrulanmadı** — halı denemesi bunu ölçemedi (halı düz ürün, yan açı kavramı anlamsız + kullanılan 4 fotoğraf gerçek 4 açı değildi). Gerçek bir mobilyanın 4 gerçek açısıyla ayrı bir test gerekiyor — **pilottan önce yapılmalı**.
  - **AI aramada oda taraması sahiplik kontrolü YOK** — giriş yapmış herhangi bir kullanıcı başkasının `roomScanId`'sini gönderip ev geometrisini alabiliyor, o veri OpenAI'a gidiyor. Temmuz'dan kalma kod; main merge turunda bulundu, kurucu kararıyla bu turun kapsamı dışında bırakıldı, ayrı iş olarak işaretlendi. **Pilottan önce kapatılmalı.**
  - **Blender render mükerrer tetikleme koruması atomik değil** — aynı render birden çok kez ücretli koşabilir. Ayrı iş olarak işaretlendi, tarih belirlenmedi.
  - **iOS Xcode'da bir kez derlenip test edilmedi**: KVKK sızıntı düzeltmesi `ios/Livaro/Models/Brand.swift`'te `ownerId` alanını opsiyonel yaptı (backend artık döndürmüyor); derleme ve cihaz doğrulaması yapılmadı.
  - Kalan artık riskler (Codex "merge-engeli değil" dedi, ama kayıtlı): çökme anına denk gelen milisaniyelik eşzamanlılık pencereleri; admin için "sadece köprüyü tekrar dene" gibi dar bir kurtarma aksiyonunun olmaması (şu an tek yol tam retry).
- Fiyat güncelliği: Excel/API ile yüklenen fiyatlar nasıl güncel tutulacak; satın alma anında fiyat değişmişse/ürün tükenmişse tasarım ne olur?
- Bkz. [[Marketplace Model]], [[Seller Experience]]

## Oda Tarama / 3D
- ~~LiDAR zorunluluğu bilinçli mi?~~ **ÇÖZÜLDÜ (2026-07-24)**: geçici kısıt; MVP LiDAR-only, LiDAR'sız çözüm ileride → [[2026-07-24 MVP yalnızca LiDAR'lı iPhone]]. Açık kalan: LiDAR'sız cihaz sahibi ilk açılışta ne yaşar (mesaj/bekleme listesi?); elle ölçü girişi (PM önerisi) denenmeli mi?
- ⭐ GPT-4o yerleşim kalitesi: **kurucu kararı (teyit turu): test MVP altyapısı/3D model tamamlandıktan sonra**; sonuca göre yol (kural tabanlı dahil). Açık: geçer/kalır ölçütü şimdiden yazılmalı mı; tam testten önce ucuz ön deneme yapılmalı mı? (PM önerileri.)
- ARKit mesh (ısınma nedeniyle kapalı) tarama-sonrası işlemeyle geri açılabilir mi?
- RoomPlan yanlış algıları (TV=pencere) için kullanıcıya düzeltme aracı gerekir mi?
- Kabul edilebilir minimum kalite çıtası ne? (Dış kullanıcı verisi sıfır.)
- Bkz. [[Room Scanning Overview]], [[3D Render Pipeline]]

## Veri / Gizlilik
- ⭐ KVKK: ev içi tarama + fotoğraflar yurt dışı işleyicilere (OpenAI, Modal, Replicate) gidiyor — açık rıza, aydınlatma metni, saklama süresi planı var mı? Dış teste çıkmadan asgari rıza + saklama politikası şart.
- ⭐ **AI aramada oda taraması sahiplik kontrolü YOK** (2026-07-31 main merge turunda bulundu): herhangi bir giriş yapmış kullanıcı başkasının `roomScanId`'sini gönderip ev geometrisini alabiliyor, o veri OpenAI'a gidiyor. Temmuz'dan kalma kod; ayrı iş olarak işaretlendi, **pilottan önce kapatılmalı** → [[2026-07-31 Kategori 3D Stratejisi, Tripo Kredi Ölçümü, iOS Doku Düzeltmesi ve Main Merge]].

## Mühendislik
- ⭐ ~~Buluta taşınma gerekli mi?~~ **KARARLAŞTI (2026-07-24)**: backend buluta taşınacak → [[2026-07-24 PM önerileri kararları — bulut taşınma, kalite çıtası, bütçe rozeti]]. Açık kalan: hangi bulut/nasıl, TestFlight zamanlaması → [[Deployment Strategy]].
- Tripo3D sonuçları cache'lenmeli (retry'lar kredi yakıyor; 24 Tem overhaul'u "stage-aware resume" tasarımı önerdi — rapor `PROJECT_STATUS.md`/import notunda); toplu yüklemeden önce 20 ürünlük kalite+maliyet denemesi yapılacak mı?
- ~~Texture regresyonlarına karşı otomatik doğrulama?~~ **Kısmen çözüldü (2026-07-24)**: kontrat karakterizasyon testleriyle donduruldu → [[E2E Testing Strategy]]; görsel çıktı (R2 içerik) doğrulaması hâlâ manuel.
- 2-3 dk'lık async render başarısız olduğunda kullanıcı ne görüyor? (Hata UX'i tanımsız.)
- ~~Eski gpt-image-1 render yolunun akıbeti; `coverageGateEnabled` bayrağı~~ — **ÇÖZÜLDÜ**: ikisi de 21+24 Tem temizlikleriyle kod tabanından çıktı (geri dönüş: `pre-cleanup-2026-07-21` tag'i).
- **Karar-kod boşlukları (24 Tem overhaul tespiti) hangi sırayla kapatılacak?** Sepet pasif listesi, yeniden-tasarla 2-hak sayacı, wizard onay adımı, %20 bütçe tavanı + rozet, render bildirimi → [[2026-07-24 Oturum Import — Mimari Overhaul Fleet]].
- Edge function'ın bulut sonrası kaderi: Nest buluta çıkınca APIConfig RELEASE URL'i Nest'e dönecek — ayna emekli mi olur, katalog cache'i mi kalır?
- brand-panel'in güncel bakım durumu (Temmuz'da hiç dokunulmadı) — çalışıyor mu? ~~2026-07-28 journey kararları mevcut panelin üstüne mi inşa edilir, yeniden mi yazılır~~ — **ÇÖZÜLDÜ (2026-07-29 build)**: yeniden yazıldı, tamamen ayrı bir site (`web/`) olarak kuruldu; brand-panel'e dokunulmadı (yalnız referans). **Güncelleme (2026-07-31):** `web/`+`admin/` main'e birleştirildi ve push edildi, ama brand-panel'in emekliye ayrılması kararı hâlâ verilmedi (merge aşamasına bırakılmıştı, merge geçti, karar hâlâ açık) → [[2026-07-31 Kategori 3D Stratejisi, Tripo Kredi Ölçümü, iOS Doku Düzeltmesi ve Main Merge]]. Açık kalan: Excel/API toplu yükleme hâlâ yapılmadı, hangi panelin üstüne inşa edileceği hâlâ belirsiz.
- Bkz. [[System Architecture]], [[Known Pitfalls]]

## Test (Testing)
- İlk otomasyon nereye: texture üretim zinciri mi, tarama→kayıt API'si mi? Bkz. [[E2E Testing Strategy]]

## Müşteri Deneyimi
- Bilinçli tasarlanmış onboarding yok — ilk açılışta kullanıcı ne görmeli? (Welcome page vizyonu var, tasarlanmadı → [[User Onboarding]].)
- Değerlendirme/puan sistemi (ürün + mağaza + AI özet) hangi eşikte devreye girecek? ("Belli kitle sonrası" — eşik tanımsız.)

## Ekip / Finansman
- Selim–Yusuf iş bölümü (teknik / marka ilişkileri / operasyon) netleşecek.
- Babalardan gelecek yatırımın meblağı ve zamanlaması; melek yatırım hedefi — **Unknown**.
- Uzun vade fikirlerinin (ünlü tasarımları, Marble/walkthrough, pazarlık ekibi) insan gücü planı — **Unknown**.

## Kayıt
- Çözülenler buradan karar/bilgi notlarına taşınır; geçmiş için Git. Kaynaklar: [[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu]], [[2026-07-24 PM Gözden Geçirme — Thinking Session]], [[2026-07-21 PM Panel Tartışması]], [[2026-07-19 Proje Kurulum Brief]].
