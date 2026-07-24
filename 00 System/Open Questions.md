---
type: system
status: living
updated: 2026-07-24
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

## Mühendislik
- ⭐ ~~Buluta taşınma gerekli mi?~~ **KARARLAŞTI (2026-07-24)**: backend buluta taşınacak → [[2026-07-24 PM önerileri kararları — bulut taşınma, kalite çıtası, bütçe rozeti]]. Açık kalan: hangi bulut/nasıl, TestFlight zamanlaması → [[Deployment Strategy]].
- Tripo3D sonuçları cache'lenmeli (retry'lar kredi yakıyor); toplu yüklemeden önce 20 ürünlük kalite+maliyet denemesi yapılacak mı?
- Texture regresyonlarına karşı otomatik doğrulama kurulacak mı?
- 2-3 dk'lık async render başarısız olduğunda kullanıcı ne görüyor? (Hata UX'i tanımsız.)
- Eski gpt-image-1 render yolunun akıbeti; `coverageGateEnabled` bayrağı.
- brand-panel'in güncel bakım durumu (Temmuz'da hiç dokunulmadı) — çalışıyor mu? Excel/API toplu yükleme bunun üstüne mi inşa edilecek?
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
