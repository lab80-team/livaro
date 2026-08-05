---
type: decision
status: accepted
created: 2026-08-06
source: "[[2026-08-06 Halı Doku Delikleri, Saçak Modeli ve Migration Kurtarması]]"
related: ["[[2026-08-05 Halı ölçüsü saçak hariç — saçak ayrı yassı şerit olarak modellenir]]", "[[2026-07-29 Kategori bazlı 3D üretim stratejisi — halı düz yüzey, mobilya Tripo devam, perde sonraya]]", "[[Seller Experience]]"]
---

# Düz üründe fotoğraf boşluğu zorunlu — birebir kırpım istisna

## Bağlam

Kurucunun gerçek katalog fotoğrafı ölçüldüğünde (1152×1516 px, halı 207×300 cm) boru hattı fotoğrafa **hiç dokunamıyordu**: beyaz pay altta yalnız 10 px, kodun arka planı örneklediği bant 46 px. Sonuç, sessiz üç kayıp:

1. Arka plan temizlenmiyor — kadrajdaki beyaz şeritler dokuya gömülü kalıyor.
2. Kadrajın oranı (0,76) halının oranından (0,69) farklı olduğu için desen boyuna **%10 geriliyor**.
3. Saçak ayrımı hiç yapılamıyor.

Kritik nokta: **germeyi kaldırmak tek başına işe yaramıyor.** Doku 0-1 aralığında ürüne kaplandığı için aynı bozulma UV eşlemesinde yeniden oluşuyor. Yani boşluksuz fotoğraftan doğru model çıkmasının yolu yok.

Ayrıca bu kusur eskiden ancak **üretim kuyruğunda, dakikalar sonra** ortaya çıkıyordu; satıcı ürünü "başarısız" olarak görüyordu.

## Karar

1. **Düz üründe (halı) fotoğrafın etrafında boşluk zorunlu.** Kontrol YÜKLEME ANINDA yapılır, üretimde değil; geçmeyen fotoğraf depoya hiç yazılmaz.
2. Zorunlu alt sınır **kenar başına kadrajın %2'si**; panelde rahat hedef olarak %5 öneriliyor.
3. **İSTİSNA: halıya birebir kırpılmış fotoğraf kabul edilir.** Mağazalar hazır katalog görselini kullanabilsin diye. Ölçüt, kadrajın oranının ürünün girilen oranıyla uyuşması.
4. Reddedilen, **arada kalmış kırpımdır**: kenarda birkaç piksel zemin artığı bırakılmış fotoğraf.

## Gerekçe

- **Boşluk zorunluluğu:** ölçüldü ki boşluksuz fotoğraf üç ayrı sessiz kalite kaybı üretiyor ve hiçbiri sonradan telafi edilemiyor.
- **Yükleme anında:** hata satıcıya anında ve ne yapması gerektiğini söyleyerek gidiyor. Aynı fotoğraf üretimde de reddedilirdi ama dakikalar sonra ve "ürün başarısız" olarak.
- **Birebir kırpım istisnası:** tam kırpılmış fotoğrafta temizlenecek arka plan zaten yok ve oran doğru; model gayet iyi çıkıyor. Katı kural bunları da geri çevirerek satıcıya boşuna yeniden çekim yaptırıyordu. Pilot için mağazaların eldeki görselleriyle başlayabilmesi belirleyici oldu.
- **%2 ile %5 farkı:** %2 teknik alt sınır (bunun altında arka planı güvenilir örnekleyemiyoruz), %5 tavsiye — sınırı tam %5 yapmak %4 boşluk bırakmış gayet iyi bir fotoğrafı boşuna reddederdi.

## Değerlendirilen Alternatifler

- **Katı kural (istisnasız boşluk zorunlu):** ilk uygulanan hâliydi. Sorunsuz çalışacak birebir kırpılmış katalog görsellerini de reddediyordu — kurucu gevşetilmesini istedi.
- **Kırpılmış fotoğrafı olduğu gibi kabul etmek (germeyi kapatarak):** işe yaramaz, çünkü germe UV eşlemesinde tekrar oluşuyor.

## Sonuçlar (Consequences)

- Kontrol hem satıcı hem admin fotoğraf değiştirme yollarında geçerli; ikisi tek paylaşılan yardımcıdan geçiyor (tipli `ModelStrategy` alıyor, geri çağrı değil — yanlış bağlama derlemede yakalansın diye).
- Kurucunun gerçek fotoğrafıyla doğrulandı: olduğu gibi hâli **red**, beyaz payı kesilmiş (birebir) hâli **kabul**, simetrik paylı hâli **kabul** (ve boru hattı payı düzgün kırpıyor, dokuya gömmüyor).
- Panel rehberi güncellendi: istisna açıkça anlatıldı, "hazır katalog görselleri genelde sıfır boşlukla kırpılmıştır" uyarısı ve reddedilenin arada kalmış kırpım olduğu yazıldı.

## Riskler

- **İstisna, halının İÇİNE kırpılmış fotoğrafı da kabul edebilir.** Bordürü kesilmiş bir fotoğraf da aynı oranı koruyabilir; o zaman eksik halı tam ölçüye yayılır. Codex bunu iki kez işaret etti; renkle ayırt edilmesi mümkün değil. **Gevşek kural kararının bilinçli bedeli** — pratikte satıcının kendi katalog görseli halının tamamını gösterdiği için düşük ihtimal, ama sıfır değil.
- Birebir kırpılmış görselde püskül zaten kesilmiş olur, dolayısıyla 3D'de de olmaz.
- Kural yalnız **düz ürünlerde** (halı) geçerli; mobilya/Tripo yolu etkilenmiyor.

## İlgili Görevler

- Gerçek satıcı fotoğraflarıyla ilk toplu yükleme sonrası kabul/red oranına bakılmalı — çok red geliyorsa eşik ya da rehber gözden geçirilir (bkz. [[Task Board]]).

## İlgili Bilgi

[[Seller Experience]] · [[Known Pitfalls]]

## Kaynak Toplantı

Bu bir toplantı kararı değil — 6 Ağustos Claude oturumunda, gerçek fotoğraf üzerinde ölçüm sonuçları ve iki seçeneğin karşılaştırması kurucuya sunuldu, kurucu "gevşek kural" dedi. Kayıt: [[2026-08-06 Halı Doku Delikleri, Saçak Modeli ve Migration Kurtarması]].
