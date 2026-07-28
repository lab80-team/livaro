---
type: system
status: living
updated: 2026-07-28
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
- Teyit turu (24 Tem) tüm bekleyen teyitleri kapattı; emanet lisanslı ödeme kuruluşuyla, iptal/iade yasaya uygun tasarlanacak (detay açık) → [[Open Questions]].
- Katalog: yalnızca 3 usdz'li test ürünü (gerçek katalog pilot markalardan dolacak; henüz hiçbir satıcıyla görüşülmedi).

## Güncel Teknik Durum
- Yığın: SwiftUI iOS + NestJS/Prisma/Supabase + Cloudflare R2 + Modal (Blender, T4) + OpenAI GPT-4o + Replicate flux-schnell + Tripo3D. Detay: [[System Architecture]].
- **Aktif 3D yolu**: RoomPlan geometri + fotoğraftan birebir kırpılan texture + Modal'da headless Blender render/USDZ. Detay: [[3D Render Pipeline]].
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
1. **Tripo ölçek/rotasyon şüphesi** (24 Tem turunda bir modelde ölçek/yerleşim tuhaflığı görüldü; GPT-4o yerleşim testiyle birlikte ele alınacak).
2. Katalog doldurma (Tripo3D'den gerçek ürünler).
3. **GPT-4o yerleşiminin kapsamlı testi** (sonuca göre teknoloji kararı — 24 Tem, cevap 14; turdaki yerleşim tuhaflığı bu testin önemini artırdı).
4. Kalan ürün belirsizliklerinin kapatılması (bekleyen teyitler, ödeme sağlayıcısı, birim maliyet) — bkz. [[Open Questions]].

> Edge function **deploy edildi ve uçtan uca doğrulandı (24 Tem)**: R2 secret'ları yüklendi; canlı API testleri geçti; **Release build telefonda uygulama içinden de doğrulandı** (katalog + 360°/AR + giriş). **İlk TestFlight yüklemesi yapıldı (25 Tem)**: build 1.0 (2026072401) App Store Connect'e çıktı; uygulama artık iPhone-only hedefli (iPad+salt-dikey reddi 90474 → MVP LiDAR-iPhone kararıyla zaten uyumlu). Apple işlemesi sonrası TestFlight'ta test edilebilir.

> Cihaz doğrulama turu (24 Tem) **7/7 tamamlandı**: 360°/AR ✓ (ilk kez), tarama+too-close ✓, yakın çekim texture akışı uçtan uca ✓, Yeniden Tasarla ✓, Render gerçek odayla ✓ (girintili floorPolygon + kapı/pencere kesimleri), AR relocalization ✓, USDZ QuickLook'ta materyallerle ✓. Detay: [[2026-07-24 Oturum Import — Mimari Overhaul Fleet]] ve [[Task Board]].

## Güncel Blocker'lar
- Bilinen aktif blocker yok. (Geçmişte: Modal kredi tükenmesi — çözüldü; Replicate kredisi — yüklendi.)

## Son Kararlar
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
- Texture pipeline regresyona açık (iki kez yaşandı) — artık karakterizasyon testleriyle korunuyor (24 Tem); görsel çıktı (R2 içerik) doğrulaması yine de manuel: [[Known Pitfalls]].
- RoomPlan'ın TV'yi pencere sanması gibi veri hataları çıktıya yansıyor.
- LiDAR'lı iPhone zorunluluğu pazarı daraltıyor (bilinçli geçici kısıt — [[2026-07-24 MVP yalnızca LiDAR'lı iPhone]]).
- PM incelemesinin (24 Tem) öne çıkardığı riskler: emanet para = lisans sorunu; "iptal yok" ↔ 14 gün cayma hakkı; AI yerleşim kalitesi ölçülmedi; birim maliyet bilinmeden ücretsiz model; kapsam-kaynak uçurumu → [[2026-07-24 PM Gözden Geçirme — Thinking Session]].
