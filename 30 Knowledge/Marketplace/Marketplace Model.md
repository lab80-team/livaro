---
type: knowledge
status: living
updated: 2026-07-24
related: []
---

# Marketplace Model

> Ticari model 2026-07-24 thinking session ile büyük ölçüde şekillendi. İlk sürüm: **sepet var, checkout ödeme teknolojisi seçilince** → [[2026-07-24 Sepet MVP'de, checkout ödeme teknolojisi seçilince]] ([[2026-07-21 İlk ürün kapsamı görselleştirme + lead|21 Tem kararını]] günceller; checkout gelene kadar sepetin davranışı **To Be Decided**).

## Gelir Modeli (kurucu planı, 2026-07-24)
- **Kısa vade: %10 komisyon** — sepetteki fiyattan, her üründen/markadan.
- **Orta vade: reklam** — mağazalar ürünlerine ve kendilerine reklam verebilecek; tarz+bütçe+renge uygun ürünler arasından reklamlı olan öne çıkacak; **"Sponsorlu" etiketiyle gösterilecek** (kurucu onayı, cevap 19). Showroom senaryosunun (kullanıcı tasarımı görüp mağazadan alırsa) gelir mantığı reklama dayanıyor — takip mekanizması **To Be Decided**.
- **Uzun vade: indirim/hizmet bedeli** — "fark cebe" pazarlık modeli **büyük ihtimalle rafa** (çıkar çatışması + faturalandırma riski). Yerine: kullanıcı indirim talebi açar, **hizmet bedeli baştan alınır** (satın almasa bile), ekip mağazayla pazarlığı yapar. **Teyit turu (2026-07-24): hizmet bedelinin baştan alınması kurucu kararı olarak korundu** (PM itirazına rağmen). Modelin detayları/zamanlaması hâlâ tasarlanacak.
- **Ek özellik satışı (uzun vade)**: video walkthrough, Marble benzeri sanal dünya — abonelik paketi veya tek kullanımlık satın alım.
- **Kullanıcıya fiyatlandırma: şimdilik ücretsiz**; maliyet kurucuların cebinden; limit ve paketler ileride. Teyit turu (2026-07-24): **toplam yeni tasarım sayısında kısa vadede sınır yok** (amaç kullanıcı çekmek; birim maliyet hesabından sonra süzgeç); yeniden tasarla 2 hak. **Birim maliyet analizi bilinçli olarak MVP hazır olunca yapılacak** — gerekçe: kullanılacak teknolojiler MVP'yle netleşir (PM'in "bu hafta hesapla" önerisinin tersine kurucu sıralaması).

## Ödeme (plan; sağlayıcı seçilmedi)
- İki yönlü: kullanıcıdan tahsilat → mağazaya ödeme. **KARAR (2026-07-24, teyit turu): emanet para lisanslı ödeme kuruluşu aracılığıyla tutulacak** — Livaro kendi hesabında emanet tutmayacak → [[2026-07-24 Emanet lisanslı ödeme kuruluşuyla]]. Sağlayıcı seçimi hâlâ açık → [[Open Questions]].
- **Stoklu** (halı, perde) ve **stoksuz/özel üretim** (mobilya) firmalar için **farklı ödeme planları**; plan kullanıcı+mağaza onaylarıyla oluşacak.
- **Özel üretimde avans**; oranı mağazalarla ihtiyaçlarına göre konuşulup belirlenecek — **To Be Decided**.
- Ödeme sağlayıcısı **To Be Decided** (Iyzico olasılık, taahhüt değil — 2026-07-21 kurucu beyanı).

## İptal / İade (plan)
- **Güncellendi (2026-07-24, teyit turu): iptal/iade yasaya uygun tasarlanacak** — "iptal yok" katı kuralı yumuşatıldı; nasıl olacağı **henüz belli değil**, araştırılacak (14 gün cayma hakkı + özel üretim istisnası dahil) → [[Open Questions]]. İade yine kullanıcı-mağaza karşılıklı onay mantığıyla kurgulanıyor.
- Defo/kırık sorumluluğu **tamamen mağazada** ("ibare geçilecek"). **İtiraz süresi 48 saat**; anlaşmazlığın mağaza-kullanıcı arasında çözüleceği varsayılıyor (hakemlik kuralı tanımsız — **To Be Decided**).
- Satın alım sonrası **kullanıcı-mağaza birebir chat'i**: telefon paylaşımı yasak, **AI denetleyecek**; onay kayıtlarının nasıl tutulacağı **To Be Decided**.

## Lojistik (plan)
- Tasarımlar çok markalı (ör. 10 marka, 20 ürün); mobilya çoğunlukla stoksuz üretim, teslimat ~1 aya kadar.
- Kullanıcıdan **teslimat tarihi tercihi** alınacak (hepsi aynı gün mü, parça parça mı); tarihler markalara **önceden bildirilecek**. Tercihin akışın neresinde sorulacağı (tasarımdan önce/sonra) **To Be Decided**.
- **Fiyatlar nakliye dahil; nakliye mağazanın sorumluluğu.** İleride Livaro'nun kendi nakliye anlaşmaları olabilir. Montaj ve "bir marka tarihe yetişemezse" senaryosu **To Be Decided**.
- Mağazalar **stoklu ürünlerde stok girecek**; özel üretimde stok takibi yok (üretilir).

## Değerlendirme Sistemi (belli kitle sonrası)
- Ürün: parametreli değerlendirme (rahatlık, kalite…), yorum, puan, **AI özet yorum** (Trendyol benzeri).
- Mağaza puanı: termin süresine uyum, soru yanıt hızı, kargoya verme süresi, kullanıcı puanı. Kullanıcı mağazaya uygulama içinden soru sorabilecek. Algoritma iyi mağazaları üste taşıyacak (ileride).
- Geciken mağaza: puanı düşer, algoritmada geriler; **2 gecikmeden sonra ceza** — oran/meblağ **To Be Decided**, kalan bakiyeden kesilir (PM itirazı: pilotta parasal ceza arzı kaçırır).

## Roller / Yapı
- Roller sistemde tanımlı: **CUSTOMER** (iOS), **SELLER** (web brand-panel), **ADMIN**. Bkz. [[2026-06-22 iOS uygulaması yalnızca müşteri tarafı]].
- **Keşfet sayfası**: pazaryeri vitrini; ilk gün pilot marka ürünleriyle dolacak. Markalar mı ürünler mi listelenecek **To Be Decided**. Kullanıcı manuel ürün seçip onlardan AI tasarım yaptırabilecek.
- Teknik altyapıda katalog + Tripo3D 3D üretim hattı hazır; katalogda 3 test ürünü (gerçek katalog pilot markalardan dolacak → [[2026-07-24 Pilot marka kriterleri]]).

## Bilinmeyenler
- ~~Checkout gelene kadar sepetin davranışı~~ — **ÇÖZÜLDÜ (2026-07-24, teyit turu)**: sepet şu anlık **pasif liste** (mağazaya talep iletilmez).
- Birim ekonomisi (render + Tripo3D + OpenAI maliyeti) — **hiç hesaplanmadı**; analiz bilinçli olarak MVP sonrasına bırakıldı.
- Showroom kaçağının takibi (indirim kodu/referans) — **To Be Decided**.
- Montaj/kurulum sorumluluğu — **To Be Decided**.

## İlgili Notlar
- [[Seller Experience]], [[Target Users]], [[Product Overview]]
- [[2026-07-24 Sepet MVP'de, checkout ödeme teknolojisi seçilince]], [[2026-07-24 Pilot marka kriterleri]]

## Kaynaklar
- [[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu]] (cevap 1, 18-28, 30, 32)
- [[2026-07-24 PM Gözden Geçirme — Thinking Session]]
