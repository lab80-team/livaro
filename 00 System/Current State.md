---
type: system
status: living
updated: 2026-08-04
---

# Current State

> Projenin **şu anki** özeti. Sürekli güncellenir. **Tarihçe tutulmaz** — geçmiş, kaynak notlarda ([[Meeting Index]], Inbox import'ları) ve Git'te.
>
> Kaynaklar: [[2026-07-19 Proje Kurulum Brief]] + üç oturum import'u (16 Haziran – 20 Temmuz dönemini kapsar) + kod reposu `PROJECT_STATUS.md`.

## Güncel Ürün Durumu
- Çalışan **iOS prototipi** var (LiDAR'lı iPhone): oda tarama (RoomPlan) → 4-8 köşe fotoğrafı → materyal analizi → texture'lı 3D oda → AI Designer wizard (tarz/bütçe) → .usdz mobilyalı tasarım sahnesi → Blender render galerisi (4 açı) + USDZ.
- **Uçtan uca vizyon kayda geçti (2026-07-24 thinking session)**: gerçek ürünlerle AI oda tasarımı + pazaryeri + operasyon aracılığı; problem hipotezi netleşti → [[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu]], [[User Problems]].
- **MVP kapsamı (21+24 Tem kararları, teyit turu dahil)**: sıfırdan tasarım (boş oda veya dolu oda AI ile boşaltılarak), ürün çıkarma (alternatifle değiştirme MVP'de yok), AR (tüm oda), **sepet MVP'de pasif liste — checkout ödeme teknolojisi seçilince**, yalnızca LiDAR'lı iPhone, bütçe aşım tavanı ~%20 (uygun tasarım yoksa), yeniden tasarla 2 hak (toplam tasarım sayısı şimdilik sınırsız), anlık deneyim = canlı 3D sahne + arka planda render. Kararlar: [[Decision Index]].
- **Hedef kullanıcı anı (2026-07-21, teyit 24 Tem)**: taşınma + tadilat/yenileme; tek parça alım ileride → [[2026-07-21 Hedef kullanıcı anı — taşınma ve tadilat]].
- **Gelir planı (2026-07-24)**: kısa vade %10 komisyon, orta vade reklam (Sponsorlu etiketli), uzun vade indirim/hizmet bedeli; şimdilik kullanıcıya ücretsiz → [[Marketplace Model]].
- **Pilot marka kriterleri kararlaştı**: her kategoriden 2 internette satan firma; mağazalara MVP bitince gidilecek → [[2026-07-24 Pilot marka kriterleri]].
- **Mağaza web paneli journey kararlaştı (2026-07-28 thinking session, 2 PM'li tartışmayla)**: self-serve kayıt + admin onayı (KVKK + satıcı sözleşmesi kutuları; şifre veya SMS girişi); ürün formu fiyat/ölçü/stok + kategoriye özel sorularla; **3D zorunlu** (Tripo 2 deneme hakkı, aşımda admin kuyruğu; 3D'siz ürün yayında olmaz); admin ürün onayı; Excel toplu yükleme; sorular herkese açık + filtreli; **sohbet MVP dışı** (checkout ile) → [[2026 07 28 Thinking Session — Mağaza Web Paneli User Journey]], [[Seller Experience]]. Açık: onay kriterleri, Tripo bütçesi, kategori soru setleri (ayrı session planlı).
- **Mağaza web sitesi + yönetim sitesi main'e birleştirildi ve push edildi (2026-07-31, `44a4497`)**: 2026-07-28 journey kararlarının uygulaması (`web/` mağaza sitesi + ayrı `admin/` yönetim sitesi) 2026-07-29'da build edildi, yerelde uçtan uca canlı doğrulandı; birleştirme öncesi zorunlu Codex inceleme kapısı **7 turda 22 açık buldu** (KVKK sızıntıları — `GET /brands` onaylanmamış başvuruların telefonu/konumunu herkese açık döndürüyordu; eski `/3d-pipeline` ucu 3D zorunluluğu ve admin onayını atlatıyordu; kredi çift-yakma ve ürünün sessizce kaybolma riskleri) — hepsi regresyon testiyle kapatıldı, 399 test yeşil, dört derleme temiz. Edge function deploy edildi ve canlı doğrulandı. **Yapısal karar**: kullanılmayan `/3d-pipeline` HTTP uç katmanı tamamen kaldırıldı (yama değil, söküm) → [[2026-07-31 Kullanılmayan 3d-pipeline HTTP uçları tamamen kaldırıldı]]. Build sırasında bulunup kurucu onayıyla düzeltilen iki hata: 3D üretimi gerçekte yalnız ilk fotoğrafı kullanıyordu (artık 4 açının tamamı, Tripo `multiview_to_model`) ve yeni foto seti eskisine ekleniyordu (artık yerine geçiyor) → [[2026-07-29 3D üretimi 4 açının tamamını kullanır — Tripo multiview_to_model]], [[2026-07-29 Yeni fotoğraf seti eskisinin yerine geçer, tekil silme yok]]. Detay: [[Seller Experience]], [[2026-07-29 Build Oturumu — Mağaza Web ve Yönetim Sitesi]], [[2026-07-31 Kategori 3D Stratejisi, Tripo Kredi Ölçümü, iOS Doku Düzeltmesi ve Main Merge]]. **Gerçek satıcı henüz kullanmadı — Validated değil.**
- **Admin panel v1 kapsamı kararlaştı (2026-08-04 thinking session, 2 PM'li tartışmayla) — henüz inşa edilmedi**: ana sayfa pilotta grafik değil iş kuyruğu (4 bekleyen sayacı + son kaydolan mağaza/kullanıcı listeleri; sütun/çizgi grafikler veri birikince); Mağazalar sekmesi kart + 3 türlü kırmızı rozet (ürün onayı + STUCK + düzenleme onayı); Ürünler sekmesi + "yayından kaldırma" (kalıcı silme yalnız yasaklı içerik); yayında yalnız vitrin alanı (foto/başlık/açıklama) değişince yeniden onay; adminde kişi bazlı kullanıcı kartı (tüm bilgiler + kullanım istatistikleri + RoomPlan çıktısı — PM'lerin KVKK itirazı kayıtlı, aydınlatma şartı); başlangıçta 2 yetkili + panelden yetkili ekleme; ciro/satış/reklam alanları veri doğana dek panelde yok → [[2026 08 04 Thinking Session — Admin Paneli]], [[Admin Panel]]. Açık: işlem günlüğü ve sessiz olay defteri (PM önerileri, onaylatılmadı), foto-3D tutarlılığı, inşa sırası → [[Open Questions]].
- **Kategori bazlı 3D üretim stratejisi kararlaştı (2026-07-29 akşamı)**: **halı artık Tripo kullanmıyor** — düz yüzey + yüksek çözünürlüklü doku (kanıt: aynı Hereke halısı Tripo'yla ve düz yüzeyle üretilip karşılaştırıldı, düz yüzey hem daha net hem 0 kredi vs Tripo ~50-70 kredi); **mobilyada Tripo `multiview_to_model` devam ediyor**, model sürümü v3.1'e çekildi ve gerçek kredi maliyeti ölçüldü (kullanılabilir kalite **60 kredi/ürün**; Tripo'nun kendi fiyat dokümanındaki P1 rakamı yanlış çıktı — 50 değil 60); **perde tedarik yolu sonraya bırakıldı** (henüz seçilmedi). → [[2026-07-29 Kategori bazlı 3D üretim stratejisi — halı düz yüzey, mobilya Tripo devam, perde sonraya]], [[Kategori bazlı 3D üretim denemeleri — halı Tripo vs düz yüzey, kanepe kredi-kalite ölçümü]].
- **iOS'ta kaybolan doku haritaları düzeltildi (2026-07-29/30)**: USDZ dönüştürücü daha önce yalnız renk dokusunu taşıyordu, normal (yüzey kabartma) ve pürüzlülük/metaliklik haritalarını sessizce atıyordu — AR'da model gerçekte olduğundan "düz" görünüyordu (4K↔8K tartışmasından çok daha büyük görsel kayıp). Ayrıca bir ölçek hatası (Tripo GLB'sindeki node transform okunmuyordu — kanepe 325×76×96 cm yerine 32,8×26,5×100 cm çıkıyordu) düzeltildi; iOS uygulamasında görünmüyordu (uygulama zaten yeniden ölçekliyor) ama AR Quick Look/paylaşılan dosya için yanlıştı. Bkz. [[Known Pitfalls]].
- **Gerçek Tripo multi-view denemesi yapıldı (2026-07-29 akşamı, kurucu onayıyla, kredi harcandı)**: bir Hereke halısıyla `TRIPO3D_FAKE=0` koşuldu — `multiview_to_model` isteği kabul edildi, model üretilip R2'ye yazıldı ve panelde döndürülerek incelendi (çıkan model orijinal halının kendisi). Yani **boru hattı gerçek Tripo'da uçtan uca çalışıyor**. Ancak ön/arka/sol/sağ eşlemesinin doğruluğu (model aynalanıyor mu) bu denemede **ölçülemedi** — halının fotoğrafları gerçek 4 açı değil; eşleme testi bir mobilyanın gerçek 4 açısıyla yapılmalı → [[Open Questions]]. (Not: halı artık zaten Tripo kullanmıyor — bu deneme, boru hattının gerçek Tripo'da uçtan uca çalıştığını kanıtlamak için değerli kaldı; sol/sağ eşleme sorusu mobilya için hâlâ açık.)
- Teyit turu (24 Tem) tüm bekleyen teyitleri kapattı; emanet lisanslı ödeme kuruluşuyla, iptal/iade yasaya uygun tasarlanacak (detay açık) → [[Open Questions]].
- Katalog: yalnızca 3 usdz'li test ürünü (gerçek katalog pilot markalardan dolacak; henüz hiçbir satıcıyla görüşülmedi).

## Güncel Teknik Durum
- Yığın: SwiftUI iOS + NestJS/Prisma/Supabase + Cloudflare R2 + Modal (Blender, T4) + OpenAI GPT-4o + Replicate flux-schnell + Tripo3D. Detay: [[System Architecture]].
- **Aktif 3D yolu**: RoomPlan geometri + fotoğraftan birebir kırpılan texture + Modal'da headless Blender render/USDZ. Detay: [[3D Render Pipeline]].
- **Ürün 3D üretimi artık kategoriye göre dallanıyor** (2026-07-29 kararı): mobilya Tripo3D `multiview_to_model` (v3.1), halı Tripo'suz düz yüzey, perde henüz seçilmedi. Kullanılmayan eski `/3d-pipeline` HTTP uç katmanı 2026-07-31'de tamamen kaldırıldı. Detay: [[Seller Experience]], [[2026-07-31 Kategori 3D Stratejisi, Tripo Kredi Ölçümü, iOS Doku Düzeltmesi ve Main Merge]].
- **Süreç dersi (31 Tem merge)**: görev-bazlı kod incelemesi (her ajan yalnız kendi diff'ine bakan) eski/kullanılmayan uçların hâlâ açık kalıp kalmadığını sormuyor — main'e birleştirme öncesi ayrı, bütünsel bir güvenlik/sızıntı turu şart oldu (7 tur, 22 bulgu). Detay: [[Known Pitfalls]].
- **Mimari overhaul (2026-07-24)**: iki-mimar fleet + Codex incelemesiyle kod tabanı 24 Tem kararlarına göre elden geçirildi (7 commit, `cleanup/dead-code`): ölü modüller söküldü (backend order/user; iOS coverage kalıntıları), güvenlik sıkılaştırıldı (kayıt yalnız CUSTOMER; presign açığı kapandı; okuma/yazma sahiplik guard'ları), 3D model URL'leri her yüzeyde presigned ("360°/AR'da Gör" ilk kez çalışır durumda — cihaz doğrulaması bekliyor), RoomScene3DView 839→467 satır, testler backend 21→39 / iOS 53→62. Detay: [[2026-07-24 Oturum Import — Mimari Overhaul Fleet|import notu]] ve kod reposu `PROJECT_STATUS.md`. Tespit edilen **karar-kod boşlukları** (bilinçli yapılmadı — özellik işi): sepet pasif listesi, yeniden-tasarla 2-hak sayacı, wizard onay adımı, %20 bütçe tavanı, render bildirimi.
- **Giriş sistemi genişledi (2026-07-28)**: telefonla SMS kodu (Twilio Verify), Google ve Apple girişleri eklendi. Supabase Auth kimliği yeni `auth/supabase` ucuyla mevcut app JWT'sine takas ediliyor (Nest + edge function aynı); users tablosunda email/şifre artık opsiyonel, phone + supabaseId kolonları eklendi. Panel: Twilio Verify bağlı, Google/Apple açık, kullanılmayan Supabase e-posta girişi güvenlik için kapatıldı. Edge function deploy edildi, canlı smoke 3/3 (OTP ucu Twilio'ya ulaşıyor). İki turlu Codex incelemesi işlendi; commit: kod reposu `cleanup/dead-code` 73c0926. Cihazda üç giriş yolu da doğrulandı (28 Tem). **Bekleyen**: yeni TestFlight build; gerçek kullanıcı SMS'i için Twilio hesabının trial'dan çıkarılması.
- Gözlem (2026-07-28): iOS **simülatöründe** uygulama açılışta beyaz "Livaro" ekranında kalıyor; eski sürümde de aynı (bu değişikliklerle ilgisi yok) ve cihazda görülmüyor. Nedeni araştırılmadı — açık.
- Backend dev ortamında kurucu Mac'inde koşuyor (mDNS); **KARAR (2026-07-24): buluta taşınacak** (arka plan render + bildirim ve kullanıcı çekme ön şartı) → [[2026-07-24 PM önerileri kararları — bulut taşınma, kalite çıtası, bütçe rozeti]]. Hangi bulut/nasıl — açık: [[Deployment Strategy]].

## Oda Tarama Durumu
- Temel: Apple RoomPlan (güvenilir). Yaklaşım geçmişi ve sonuçları: [[Room Scanning Approaches]] (gsplat başarısız→rafta; ARKit mesh çalıştı→offline; RoomPlan+AI texture aktif).
- Zemin/duvar yakın çekim adımları **cihazda uçtan uca doğrulandı (24 Tem)**: floor.jpg gerçek parke fotoğrafından kırpılıyor, manifest sözleşmeye uygun. Gözlem: kırpılan fotoğraftaki ışık farkı karo tekrarında ızgara deseni olarak görünüyor (aynalı karo yönteminin bilinen takası — kabul edilebilirliği değerlendirilecek, [[Task Board]]).

## Çalıştığı Bilinenler
- RoomPlan tarama + saf Transform render; Kat Planı/Roomplan/Render sekmeleri; AI Designer wizard (4 adım; pgvector + GPT-4o iç mimar rolü + yerleşim doğrulama); Blender pipeline (test odası + gerçek oda render'ları); fotoğraftan texture kırpma + mirror tile; Tripo3D ürün 3D kuyruğu; brand-panel satıcı ürün yükleme (Haziran'da uçtan uca doğrulandı; güncel durumu Needs Validation); LivaroTheme tasarım sistemi; mDNS bağlantı; presigned R2 akışı.

## Başarısız / Rafta Olduğu Bilinenler
- Gaussian Splatting (ARKit pozları yetersiz — kanıtlı; rafta, kod duruyor).
- ARKit Scene Reconstruction mesh+texture (çalıştı; ısınma/crash → bayrakla kapalı).
- Generatif fotogerçekçi render (gpt-image-1/ControlNet — geometri sadakati yok; superseded).
- Detay: [[Experiment Index]].

## Güncel Öncelikler (Now)
1. **iOS'un Xcode'da bir kez derlenip test edilmesi** (KVKK sızıntı düzeltmesi `Brand.swift`'te bir alanı opsiyonel yaptı, henüz canlı doğrulanmadı).
2. **Mobilyada Tripo sol/sağ eşleme doğrulaması** — gerçek 4 açılı bir ürünle, pilottan önce.
3. **Perde tedarik yolu seçimi** (hazır kıvrımlı model kütüphanesi — freelancer mı, hazır asset mi).
4. **Tripo ölçek/rotasyon şüphesi** (24 Tem turunda bir modelde ölçek/yerleşim tuhaflığı görüldü; GPT-4o yerleşim testiyle birlikte ele alınacak).
5. Katalog doldurma (Tripo3D'den gerçek ürünler; mobilya artık ~60 kredi/ürün maliyetiyle).
6. **GPT-4o yerleşiminin kapsamlı testi** (sonuca göre teknoloji kararı — 24 Tem, cevap 14; turdaki yerleşim tuhaflığı bu testin önemini artırdı).
7. Kalan ürün belirsizliklerinin kapatılması (bekleyen teyitler, ödeme sağlayıcısı, birim maliyet) — bkz. [[Open Questions]].

> Edge function **deploy edildi ve uçtan uca doğrulandı (24 Tem)**: R2 secret'ları yüklendi; canlı API testleri geçti; **Release build telefonda uygulama içinden de doğrulandı** (katalog + 360°/AR + giriş). **İlk TestFlight yüklemesi yapıldı (25 Tem)**: build 1.0 (2026072401) App Store Connect'e çıktı; uygulama artık iPhone-only hedefli (iPad+salt-dikey reddi 90474 → MVP LiDAR-iPhone kararıyla zaten uyumlu). Apple işlemesi sonrası TestFlight'ta test edilebilir.

> Cihaz doğrulama turu (24 Tem) **7/7 tamamlandı**: 360°/AR ✓ (ilk kez), tarama+too-close ✓, yakın çekim texture akışı uçtan uca ✓, Yeniden Tasarla ✓, Render gerçek odayla ✓ (girintili floorPolygon + kapı/pencere kesimleri), AR relocalization ✓, USDZ QuickLook'ta materyallerle ✓. Detay: [[2026-07-24 Oturum Import — Mimari Overhaul Fleet]] ve [[Task Board]].

## Güncel Blocker'lar
- Geliştirmeyi durduran aktif blocker yok. 31 Tem merge incelemesinin bulduğu iki pilot-öncesi iş **2026-08-02'de kapatıldı** (oda taraması sahiplik kontrolü + atomik render kilidi; main `0477596`, 415 test yeşil, 6 tur Codex incelemesi) → [[2026-08-02 Güvenlik Düzeltmeleri — Oda Taraması Sahipliği ve Render Kilidi]].
- Geçmişte: R2 bucket CORS eksikliği (29 Tem bulgusu — 3D model tarayıcıda yüklenmiyordu; kurucu Cloudflare panelinden CORS politikasını ekledi, aynı gün canlı doğrulandı: model indi ve döndürüldü); Modal kredi tükenmesi — çözüldü; Replicate kredisi — yüklendi.

## Son Kararlar
- [[2026-08-04 Admin panel v1 kapsamı — kuyruk ana sayfa, mağaza kartları, ciro-reklam alanları yok]] (+ aynı session'dan 4 karar daha: yayından kaldırma, vitrin onayı, kullanıcı kartı, hesap yönetimi → [[Decision Index]])
- [[2026-07-31 Kullanılmayan 3d-pipeline HTTP uçları tamamen kaldırıldı]]
- [[2026-07-29 Kategori bazlı 3D üretim stratejisi — halı düz yüzey, mobilya Tripo devam, perde sonraya]]
- [[2026-07-29 3D üretimi 4 açının tamamını kullanır — Tripo multiview_to_model]]
- [[2026-07-29 Yeni fotoğraf seti eskisinin yerine geçer, tekil silme yok]]
- [[2026-07-28 Mağaza kaydı self-serve + admin onayı]]
- [[2026-07-28 Ürün yükleme ve panel — 3D zorunlu, Tripo 2 hak]]
- [[2026-07-28 Mağaza iletişimi — herkese açık sorular, sohbet MVP dışı]]
- [[2026-07-24 PM önerileri kararları — bulut taşınma, kalite çıtası, bütçe rozeti]]
- [[2026-07-24 Anlık deneyim — canlı 3D sahne, render arka planda]]
- [[2026-07-24 Emanet lisanslı ödeme kuruluşuyla]]
- [[2026-07-24 Sepet MVP'de, checkout ödeme teknolojisi seçilince]] (sepet şu anlık pasif liste)
- [[2026-07-24 MVP yalnızca LiDAR'lı iPhone]]
- [[2026-07-24 MVP tasarım kapsamı — oda boşaltılır, sıfırdan tasarım]]
- [[2026-07-24 Bütçe aşım tavanı yüzde 10]] (tavan %20'ye güncellendi)
- [[2026-07-24 Pilot marka kriterleri]]
- Tam liste: [[Decision Index]].

## Bilinen Riskler / Dikkat
- **Mobilyada Tripo sol/sağ eşleme doğrulanmadı** — gerçek 4 açılı ürünle test edilmeden pilotta aynalanmış model riski var.
- Texture pipeline regresyona açık (iki kez yaşandı) — artık karakterizasyon testleriyle korunuyor (24 Tem); görsel çıktı (R2 içerik) doğrulaması yine de manuel: [[Known Pitfalls]].
- RoomPlan'ın TV'yi pencere sanması gibi veri hataları çıktıya yansıyor.
- LiDAR'lı iPhone zorunluluğu pazarı daraltıyor (bilinçli geçici kısıt — [[2026-07-24 MVP yalnızca LiDAR'lı iPhone]]).
- PM incelemesinin (24 Tem) öne çıkardığı riskler: emanet para = lisans sorunu; "iptal yok" ↔ 14 gün cayma hakkı; AI yerleşim kalitesi ölçülmedi; birim maliyet bilinmeden ücretsiz model; kapsam-kaynak uçurumu → [[2026-07-24 PM Gözden Geçirme — Thinking Session]].
