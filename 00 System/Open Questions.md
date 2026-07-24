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

## Kuruculara bekleyen teyitler (2026-07-24 oturumundan)
- ⭐ **Alternatifle değiştirme MVP'de mi?** Anlatımda "alternatifleri görme/değiştirme MVP'de olmasın" denildi; cevap 9'da "ürünü alternatif ile değiştirebilir" denildi. Çelişki kayıtlı, hangisi geçerli?
- ⭐ **Checkout gelene kadar sepet nasıl davranacak?** Sepete eklenen ürünler mağazaya talep (lead) olarak iletilecek mi, yoksa pasif liste mi? 21 Tem kararındaki "ince lead katmanı"nın akıbeti buna bağlı → [[2026-07-24 Sepet MVP'de, checkout ödeme teknolojisi seçilince]].
- **Anlık + gerçekçi görüntü stratejisi**: Claude/PM önerisi (canlı 3D sahnede anlık değişiklik; fotogerçekçi render arka planda "hazır" bildirimiyle; tek ürün değişimi tam render tetiklemez) kurucularca benimsenecek mi?

## Ürün (Product)
- ~~İlk ürün ne olmalı?~~ **ÇÖZÜLDÜ** (2026-07-21 + 2026-07-24): görselleştirme + sepet; checkout ödeme teknolojisi seçilince → [[2026-07-24 Sepet MVP'de, checkout ödeme teknolojisi seçilince]].
- ~~MVP tasarım kapsamı?~~ **ÇÖZÜLDÜ (2026-07-24)**: dolu oda boşaltılır, sıfırdan tasarım; ürün çıkarma var; AR tüm oda; yeniden tasarla 2 hak → [[2026-07-24 MVP tasarım kapsamı — oda boşaltılır, sıfırdan tasarım]].
- ⭐ İlk 30 kullanıcı hangi kanaldan gelecek? Kurucu beyanı (2026-07-24): ilk test kendi çevrede; **B2C go-to-market belli değil**.
- Hangi akışlar basit kalmalı? (6 adımlık tarama akışının terk oranı ölçülmedi.)
- Bütçe aşıldığında/bütçeye uygun tasarım bulunamadığında kullanıcıya ne gösterilecek? ("Çok düşük bütçe" eşiği tanımsız → [[2026-07-24 Bütçe aşım tavanı yüzde 10]].)
- "Dolu odayı dijital boşaltma" teknik olarak nasıl yapılacak? (PM alternatifi: MVP'de "boş odanı tara" demek.)
- Teslimat tarihi tercihi akışın neresinde sorulacak (tasarımdan önce mi sonra mı)?
- Bkz. [[Product Overview]], [[60 Planning/Product Flows|Product Flows]]

## Pazaryeri / İş Modeli
- ⭐ **Ödeme sağlayıcısı/teknolojisi ne olacak?** (Iyzico olasılık, karar değil.) ⚠️ Bağlı soru: "para Livaro'da emanet" planı lisanslı ödeme kuruluşu gerektirir — sağlayıcının aracı/emanet hesabı mı kullanılacak? PM: bu seçim MVP sıralamasında öne alınmalı → [[2026-07-24 PM Gözden Geçirme — Thinking Session]].
- ⭐ **"İptal yok, iade karşılıklı onayla" kuralı 14 gün yasal cayma hakkıyla nasıl bağdaşacak?** Stoklu/özel üretim ayrımı nasıl tanımlanacak? (Kurucu: araştırılacak. PM önerisi: e-ticaret avukatından pilot paketi.)
- ⭐ Render + Tripo3D + OpenAI kullanım başına maliyet ne? (Birim ekonomisi hiç hesaplanmadı; "şimdilik ücretsiz + limit ileride" kararı bu sayıya muhtaç. PM: kişi başı sayaç ilk sürümde olmalı.)
- Avans oranı ne olacak? (Mağazalarla konuşulup belirlenecek.) Gecikme cezasının oranı/meblağı?
- Defo anlaşmazlığında hakemlik: 48 saat itiraz penceresi var; mağaza kabul etmezse son kararı kim verir? Emanetteki para hangi kuralla serbest bırakılır? Geri taşıma masrafı kimde?
- Çok markalı sepette bir marka teslim tarihine yetişemezse süreç ne? Montaj/kurulum kimin sorumluluğu?
- Chat'te karşılıklı onayın kaydı (fiyat/ölçü/tarih tek yerde) nasıl tutulacak? Platform dışına kaçış (telefon yasağını AI denetleyecek) yeterli mi?
- Showroom kaçağı: kullanıcının mağazadan alımı nasıl takip edilecek (indirim kodu/referans)? Reklam geliri bunu gerçekten telafi eder mi?
- Hizmet bedelli indirim modeli (uzun vade fikri) yaşayacak mı? (PM: MVP'den tamamen çıkarılmalı; bedel ancak başarıda alınmalı.)
- Reklamın tasarım algoritmasına gömülmesi (kurucu planı) ↔ tasarım tarafsızlığı (PM itirazı) — nihai kural ne?
- ⭐ İlk satıcı görüşmesi ne zaman? (Karar: MVP bitince. PM önerisi: MVP bitmeden 5-10 firmayla ön görüşme + 1 sayfalık pilot teklifi.) Pilot kategori listesi (kaç kategori × 2 firma) netleşmedi.
- Fiyat güncelliği: Excel/API ile yüklenen fiyatlar nasıl güncel tutulacak; satın alma anında fiyat değişmişse/ürün tükenmişse tasarım ne olur?
- Bkz. [[Marketplace Model]], [[Seller Experience]]

## Oda Tarama / 3D
- ~~LiDAR zorunluluğu bilinçli mi?~~ **ÇÖZÜLDÜ (2026-07-24)**: geçici kısıt; MVP LiDAR-only, LiDAR'sız çözüm ileride → [[2026-07-24 MVP yalnızca LiDAR'lı iPhone]]. Açık kalan: LiDAR'sız cihaz sahibi ilk açılışta ne yaşar (mesaj/bekleme listesi?); elle ölçü girişi (PM önerisi) denenmeli mi?
- ⭐ GPT-4o yerleşim kalitesi: kapsamlı test edilecek (kurucu, cevap 14) — geçer/kalır ölçütü ne olacak; kural tabanlı sisteme geçiş eşiği ne? (PM önerisi: 10-30 oda × tarz, geçti/kaldı listesi.)
- ARKit mesh (ısınma nedeniyle kapalı) tarama-sonrası işlemeyle geri açılabilir mi?
- RoomPlan yanlış algıları (TV=pencere) için kullanıcıya düzeltme aracı gerekir mi?
- Kabul edilebilir minimum kalite çıtası ne? (Dış kullanıcı verisi sıfır.)
- Bkz. [[Room Scanning Overview]], [[3D Render Pipeline]]

## Veri / Gizlilik
- ⭐ KVKK: ev içi tarama + fotoğraflar yurt dışı işleyicilere (OpenAI, Modal, Replicate) gidiyor — açık rıza, aydınlatma metni, saklama süresi planı var mı? Dış teste çıkmadan asgari rıza + saklama politikası şart.

## Mühendislik
- ⭐ TestFlight ve production deployment'ın önündeki somut engel ne? (Backend hâlâ kurucu Mac'inde; PM: çevre pilotundan önce bulut + TestFlight.)
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
