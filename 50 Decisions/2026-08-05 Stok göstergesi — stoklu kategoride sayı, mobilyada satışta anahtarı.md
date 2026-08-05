---
type: decision
status: accepted
created: 2026-08-05
source: "[[2026 08 05 Thinking Session — Mağaza Paneli 3D İlerleme ve Stok Göstergesi]]"
related: []
---

# Stok göstergesi — stoklu kategoride sayı, mobilyada satışta anahtarı

## Bağlam
Kurucu, ürün listesindeki "Stokta yok" rozeti yerine **stok adedinin küçük bir kutucukta** görünmesini istedi ("sıfırsa sıfır, birse bir gibi"). Kodda ölçülen bugünkü durum:
- Stok adedi düz metin olarak yazılıyor ("Stok: 5"), yanında elle açılıp kapatılan ayrı bir "stokta yok" işareti var.
- **Mobilyada stok hiç sorulmuyor** (mobilya `stocked: false` — bilinçli, sipariş üzerine üretim). Yani her mobilya ürününün stoku veritabanında 0. Stoklu kategoriler halı ve perde.
- **Ürünü müşteriden gizleyen tek şey elle basılan "stokta yok" işareti.** Yayın filtreleri her yerde "yayında + stokta yok işareti basılı değil" diyor; **stok adedi hiçbir filtreye girmiyor.** Yani bugün "Stok: 0" yazan ürün müşteriye satılmaya devam ediyor.

Bu yüzden isteğin düz uygulanması ters çalışırdı: bütün mobilyalar kırmızı "0" rozeti alırdı.

## Karar
Kategoriye göre iki farklı gösterge:
- **Stok sorulan kategorilerde (halı, perde):** küçük **sayı kutucuğu** — 0 ise 0, 1 ise 1. Sayı sıfıra düşünce ürün müşteriye **otomatik kapanır**.
- **Stok sorulmayan kategoride (mobilya):** sayı yerine **"Satışta / Satışta değil" anahtarı**.

Böylece hiçbir kategori göstergesiz kalmaz ve mobilyaya anlamsız bir "0" yazılmaz.

## Gerekçe
Kurucunun asıl istediği, satıcının ürününü satışa açıp kapatabildiğini **tek bakışta görmesi**. Stoklu kategoride bunun doğal dili sayı, stoksuz kategoride ise açık/kapalı anahtarı. Mobilyaya stok sorusu eklemek satıcıya anlamsız bir soru sormak olurdu (sipariş üzerine üretimde stok kavramı yok).

Ayrıca sayı ile işaretin anlamı farklıdır: **sayı = "kaç adet var", anahtar = "şu an satmıyorum"**. Mağaza stoku olduğu hâlde ürünü geçici kapatmak isteyebilir (yanlış fiyat, fotoğraf yenileme, tedarik sorunu, tatil) — sayı bunu ifade edemez.

## Değerlendirilen Alternatifler
- **Sadece halı ve perdede sayı, mobilyada bugünkü "stokta yok" düğmesi aynen kalsın** (PM B) — reddedildi: en çok ürünün olduğu kategoride kurucunun isteği hiç uygulanmamış olurdu.
- **Mobilyaya da stok sorusu ekle** — reddedildi: satıcıya anlamsız soru.
- **"Stokta yok" düğmesi tamamen kalksın, sayı tek doğru kaynak olsun** (PM A'nın ilk önerisi) — reddedildi: mobilyada stok hep 0 olduğu için bu kural **bütün mobilya kataloğunu düşürürdü**.
- **Sayı sadece bilgi olsun, gizleme her yerde elle kalsın** — reddedildi: bugünkü "stok 0 ama ürün satışta" çelişkisi sürerdi.

## Sonuçlar (Consequences)
- **Yayın filtrelerine stok koşulu eklenecek** — bugün stok adedi hiçbir filtrede yok. Filtre en az beş yerde tanımlı (ürün servisi, marka servisi, kumaş servisi, AI tasarım servisi ve Supabase ayna fonksiyonu); hepsi birlikte güncellenmeli, yoksa ürün bir yerde gizlenip başka yerde görünür.
- Stok koşulu **yalnız stoklu kategorilerde** uygulanmalı — mobilyaya uygulanırsa tüm mobilya kataloğu düşer.
- Mobilyadaki anahtar bugünkü "stokta yok" işaretinin görünen yüzü olacak; arkasındaki veri aynı kalabilir.

## Riskler
- Filtrelerden biri güncellenmeden kalırsa ürün bazı ekranlarda gizli, bazılarında görünür olur — sessiz ve fark edilmesi zor bir hata sınıfı.
- Kategori listesi hâlâ geçici (mobilya/halı/perde) ve ayrı bir thinking session'da yeniden ele alınacak; yeni kategoriler geldiğinde "stoklu mu" bilgisinin doğru kurulması gerekir.

## İlgili Görevler
- Stok göstergesini değiştir (stoklu kategoride sayı + sıfırda otomatik gizleme; mobilyada satışta anahtarı) → [[Task Board]]

## İlgili Bilgi
- [[Seller Experience]], [[Marketplace Model]]

## Kaynak Toplantı
- [[2026 08 05 Thinking Session — Mağaza Paneli 3D İlerleme ve Stok Göstergesi]] (soru 2)
