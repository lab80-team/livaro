---
type: decision
status: accepted
created: 2026-08-06
source: "[[2026 08 06 Thinking Session — Uygulama User Journey]]"
related: []
---

# Favorileme Keşfet üzerinden; Sepet ekranı MVP'de yapılır

## Bağlam
Oturumun ilk turunda Favoriler ve Sepet'in bugün **ekran değil, özellik olarak yok** olduğu tespit edildi (iki ekran da boş yer tutucu; veritabanında favori/sepet tablosu bile yok). Kurucuya bunun journey'nin en büyük gizli maliyeti olduğu söylendi. Kurucu ikisinin kapsamını netleştirdi.

## Karar

### Favoriler
1. **Favorileme Keşfet üzerinden yapılır**: Keşfet'teki ürün kartlarının sağ üstündeki kalp ikonu ve ürün detay sayfasındaki kalp.
2. **Favoriler sayfası** bu ürünleri dikey listede gösterir (görsel, ad, fiyat, dolu kırmızı kalp) — paylaşılan görseldeki gibi.
3. Sepet satırlarındaki kalp de (görselde var) aynı favori listesine yazar.
4. "Odalar" sekmesi MVP'de yok → [[2026-08-06 Favorilerde Odalar sekmesi ileride — MVP'de sekme çubuğu yok]].

### Sepet
1. **Sepet ekranı MVP'de yapılır** — paylaşılan görseldeki düzenle: satırlar (görsel, ad, fiyat, −/adet/+, kalp), Ara Toplam / Kargo / Toplam.
2. **Arkasındaki sistem aşama aşama doldurulacak**: önce ekran ve sepete ekleme çalışır; sipariş/ödeme tarafı ödeme sağlayıcısı seçilince gelir.
3. **Ödeme butonu yok** — yerinde dürüst bilgi satırı → [[2026-08-06 Sepette ödeme butonu yok — dürüst bilgi satırı]].
4. Varyant yok, adet var → [[2026-08-06 Ürün varyantı MVP dışı — ileride eklenecek]].

## Gerekçe
- Favorileme için tek ve net bir kaynak belirlemek, "ürün nereden favoriye ekleniyor" sorusunu kapatıyor; Keşfet zaten katalogla karşılaşılan yer.
- Sepet ekranı, tasarım sonuç ekranındaki "Tümünü Sepete Ekle" akışının varış noktası — o akış çalışacaksa sepet ekranı MVP'de olmak zorunda.

## Değerlendirilen Alternatifler
- Sepeti tamamen MVP dışı bırakmak: "Tümünü Sepete Ekle" butonunun gidecek yeri kalmazdı.

## Sonuçlar (Consequences)
- Favoriler ve sepet için **veritabanı tabloları ve uçları sıfırdan yazılacak** (bugün hiç yok).
- Alt sekmedeki Sepet ikonunda sayı rozeti gerekiyor.
- Boş durum metinleri yazılacak (Favoriler boş / Sepet boş).
- Misafirken eklenen favori/sepet öğesinin giriş sonrası hesaba taşınıp taşınmayacağı hâlâ **açık** → [[Open Questions]].

## Riskler
- Sepet ekranı "gerçek" göründüğü hâlde arkasında sipariş olmaması, kullanıcıda satın alma beklentisi yaratır; dürüst bilgi satırı bunu karşılamak için var.

## İlgili Görevler
→ [[Task Board]]

## İlgili Bilgi
[[30 Knowledge/Product/Product Flows|Product Flows (Knowledge)]], [[Marketplace Model]]

## Kaynak Toplantı
[[2026 08 06 Thinking Session — Uygulama User Journey]] (Bölüm 4)
