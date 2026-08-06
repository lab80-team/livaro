---
type: decision
status: accepted
created: 2026-08-06
source: "[[2026 08 06 Thinking Session — Uygulama User Journey]]"
related: []
---

# Ürün varyantı MVP dışı — ileride eklenecek

## Bağlam
Kurucunun paylaştığı sepet görselinde ürün satırlarında varyant ("Bej Keten", "90x60 cm") ve −/1/+ adet sayacı vardı. Bugün sistemde bir ürün = **tek fiyat + tek ölçü + tek 3D model** ([[2026-07-28 Ürün yükleme ve panel — 3D zorunlu, Tripo 2 hak]]).

Oturumda kurucu önce "tam varyant, her seçeneğe ayrı 3D model" ve ardından "pilot öncesi, MVP'nin parçası olsun" dedi. Sonuçlar önüne konduktan sonra (31 Temmuz'da main'e birleştirilen mağaza panelinin yeniden yazılması + katalog 3D maliyetinin varyant sayısı kadar çarpılması + MVP'nin gecikmesi) kurucu kararı **aynı oturumda geri aldı**.

## Karar
1. **Varyant (renk/kumaş/ölçü seçeneği) MVP'de YOK.** İleride eklenecek.
2. **Ürün = tek fiyat + tek ölçü + tek 3D model** olarak kalıyor; mağaza paneli, 3D üretimi ve admin onay akışı **değişmiyor**.
3. Sepet görselindeki "Bej Keten" / "90x60 cm" gibi yazılar, ayrı bir seçenek değil **ürünün kendi adının/ölçüsünün parçası** olarak gösterilir.
4. Adet (−/1/+) sepette kalır.

## Gerekçe
- 31 Temmuz'da main'e birleştirilmiş, canlı doğrulanmış bir mağaza panelini yeniden yazmak MVP'yi belirgin şekilde geciktirirdi.
- Katalog 3D maliyeti varyant sayısı kadar çarpılıyordu (mobilyada ~60 Tripo kredisi/model; 3 renkli koltuk = 180 kredi) ve bugün aylık harcama tavanı yok.
- Pilot-öncesi zorunlu işler (Tripo sol/sağ eşleme doğrulaması, katalog doldurma, GPT-4o yerleşim testi) hâlâ bitmedi; varyant bunların önüne geçemezdi.

## Değerlendirilen Alternatifler
- **Tam varyant, her seçeneğe ayrı 3D, pilot öncesi**: oturumda önce seçildi, sonuçları görülünce geri alındı.
- **Varyant yazı olarak görünsün, 3D tek kalsın**: mağaza paneline küçük bir ekleme yeterdi; odadaki görünüm seçilen renge göre değişmezdi. Bugün için de reddedildi — varyantın tamamı sonraya bırakıldı.

## Sonuçlar (Consequences)
- Mağaza paneli, 3D üretim zinciri, admin onay akışı ve Excel şablonu **bugünkü hâliyle kalıyor** — yeniden yazma yok.
- Katalog 3D maliyeti öngörülebilir kalıyor (ürün başına tek model).
- iOS ürün detay ve sepet ekranlarında varyant seçici olmayacak.
- Varyant geldiğinde açılacak sorular: her varyanta ayrı 3D mi yoksa tek model + renk değişimi mi; Tripo harcama tavanı; mağaza panelindeki ürün formunun yeni hâli → [[Open Questions]].

## Riskler
- Gerçek mobilya mağazaları ürünlerini çoğunlukla **çok renkli/çok kumaşlı** satıyor. Pilotta mağazalar aynı koltuğu 3 ayrı ürün olarak yüklemek zorunda kalabilir; bu, katalogda tekrar ve kafa karışıklığı üretir. Pilot mağaza görüşmelerinde bu davranış ölçülmeli.

## İlgili Görevler
→ [[Task Board]]

## İlgili Bilgi
[[Seller Experience]], [[30 Knowledge/Product/Product Flows|Product Flows (Knowledge)]]

## Kaynak Toplantı
[[2026 08 06 Thinking Session — Uygulama User Journey]] (Bölüm 3 cevap 12-14 + Bölüm 4 düzeltmesi)
