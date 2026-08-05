---
type: decision
status: accepted
created: 2026-08-05
source: "[[2026 08 05 Thinking Session — Mağaza Paneli 3D İlerleme ve Stok Göstergesi]]"
related: ["[[2026-08-05 3D süre yazısı — önce tahmin, 20 üretim sonra gerçek ortalama]]"]
---

# 3D ilerleme göstergesi — her sayfada kapatılabilir kutucuk

## Bağlam
Bugün mağaza fotoğrafları yükleyip 3D üretimini başlattığında tarayıcının `alert()` kutusu çıkıyor ("3D üretim başladı. Kalan hak: 1"), sonra ürün listesine yönlendiriliyor. İlerleme göstergesi, süre beklentisi ve bitiş bildirimi yok; liste kendiliğinden bile yenilenmiyor. Kurucu bunun yerine yüzdeli bir ekran ve kapatılabilir bir kutucuk istedi — kapatınca üretim arka planda sürecek ve mağaza panelde gezinebilecek.

Üretimin arka planda sürmesi zaten çalışıyor (iş sunucu tarafında kuyrukta yapılıyor, tarayıcı kapansa bile devam eder). Eksik olan yalnızca göstergedir. İlerleme yüzdesi de elde var: Tripo3D iş durumu sorulduğunda 0-100 arası bir sayı gönderiyor, ama bu sayı bugün hiçbir yere kaydedilmiyor ve panele hiç gitmiyor.

## Karar
**Yer ve kapatma**
- Kutucuk panelin **her sayfasında** görünür (sağ alt).
- Mağaza kutucuğu kapatabilir. Kapatınca **üst çubukta küçük bir iz kalır** (kaç ürün üretildiği), tıklayınca kutucuk geri açılır.
- Kapatmak üretimi durdurmaz.

**İçerik**
- Yüzde + "3D modeliniz oluşturuluyor" + süre yazısı (bkz. [[2026-08-05 3D süre yazısı — önce tahmin, 20 üretim sonra gerçek ortalama]]).
- **Birden fazla ürün varsa:** başlıkta "3 ürün üretiliyor", altında en fazla 3 satır. Üretilen üründe yüzde, bekleyen ürünlerde **"sırada bekliyor"** — bekleyene süre sözü verilmez (işler sırayla yapılıyor).

**Bitiş ve hata**
- **Bitince kutucuk kaybolmaz**: yeşile döner, "3D modeliniz hazır — inceleyin" bağlantısı olur ve ürün listesi kendiliğinden yenilenir.
- **Hatada iki ayrı mesaj:** deneme hakkı kaldıysa "Olmadı — 1 hakkınız kaldı, tekrar deneyin"; hak bittiyse "Ekibimiz devraldı, sizden bir şey beklenmiyor".

## Gerekçe
- Kurucu "site içerisinde gezebilecek" dediği için kutucuğu tek sayfaya hapsetmek isteği boşa çıkarırdı.
- Kapatılan kutucuğun geri gelme yolu olmazsa mağaza tek takip aracını kendi eliyle yok eder.
- Bitişte kutucuğun kaybolmaması bilinçli: bugün hiçbir bitiş bildirimi yok ve bu, ürünlerin "mağaza onayı bekliyor"da takılı kalmasının başlıca sebebi.
- İki hata mesajının ayrılması gerekiyor çünkü iki durumun sonucu farklı: hakkı kalan mağazanın yapacağı bir iş var, hakkı bitenin yok.

## Değerlendirilen Alternatifler
- **Sadece "Ürünlerim" sayfasında** (PM B'nin ilk önerisi) — sunucu yükü gerekçesiyle savunuldu, PM B kendisi geri çekti: yükün kaynağı kutucuğun yeri değil, bugünkü yöntem (3D inceleme sayfası 5 saniyede bir tüm ürün listesini çekiyor).
- **Her sayfada ama kapatılınca bir daha gelmesin** — reddedildi.
- **Bitince kutucuk kaybolsun** — reddedildi (yukarıdaki gerekçe).

## Sonuçlar (Consequences)
- Tripo'nun ilerleme yüzdesi veritabanına kaydedilecek (bugün 3D kaydında böyle bir alan yok).
- **Yalnız üretimdeki ürünleri dönen ayrı ve hafif bir veri ucu** açılacak: tüm ürün listesi çekilmeyecek, aralık 10-15 saniye olacak, sekme arka plandayken sorgu duracak. Böylece kutucuk her sayfada yaşarken yük bugünkünün altına iner.
- Yeni uçta **mağaza sahiplik kontrolü birebir tekrarlanacak** — başka mağazanın üretimi görünmemeli. Ayrıca uç yalnız yüzde ve durum dönecek; iç iş numarası, sahiplik işareti ve ham hata metni dönmeyecek (bugün ürün listesi bunları mağazaya gönderiyor).
- İlerleme yazımı, mevcut sahiplik kilidinden geçmeli: sahipliğini kaybetmiş eski bir işçi yanlış yüzde yazmamalı. Yeni deneme başlarken yüzde sıfırlanmalı.

## Riskler
- **Yüzde 100 = bitti değil.** Tripo bitirdikten sonra indirme, gerçek cm ölçüsüne büyütme, iPhone formatına çevirme ve depoya yükleme var. Ekran %100'de donabilir. Çözüm yolu (yüzdeyi 0-90'a sıkıştırmak mı, sona "son hazırlıklar" adımı mı) **To Be Decided** → [[Open Questions]].
- **Halıda gösterilecek yüzde yok** (Tripo'ya hiç uğramıyor). PM'ler "yüzde yerine sadece 'hazırlanıyor' yazsın" diye anlaştı ama kurucuya sorulmadı → [[Open Questions]].
- 30 dakikadır üretimde kalan ürünün "takıldı" sayılması kuralı kutucuğa nasıl yansıyacak — tanımsız → [[Open Questions]].
- Panel kapalıyken bitiş bildirimi hâlâ yok; e-posta altyapısı gerçek mail atmıyor.

## İlgili Görevler
- Tripo'nun ilerleme yüzdesini kaydet + hafif ilerleme ucuyla panele taşı → [[Task Board]]
- İlerleme kutucuğunu panelin her sayfasına ekle → [[Task Board]]

## İlgili Bilgi
- [[Seller Experience]], [[Known Pitfalls]], [[System Architecture]]

## Kaynak Toplantı
- [[2026 08 05 Thinking Session — Mağaza Paneli 3D İlerleme ve Stok Göstergesi]] (sorular 4, 5, 6)
