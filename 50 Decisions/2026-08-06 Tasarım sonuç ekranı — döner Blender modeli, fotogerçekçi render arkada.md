---
type: decision
status: accepted
created: 2026-08-06
source: "[[2026 08 06 Thinking Session — Uygulama User Journey]]"
related: []
---

# Tasarım sonuç ekranı — döner Blender modeli, fotogerçekçi render arkada

## Bağlam
Kurucu tasarım sonucunun "Blender çıktısı üzerinden" gösterilmesini, çıktının fotogerçekçi olmasını ve kullanıcının "sanki canlı bir 3D formatındaymış gibi" görmesini istedi.

Yöneticiler bu isteğin içindeki gerilimi ayırdı: **fotogerçekçi görüntü bir fotoğraftır** (döndürülemez, her açı ayrı üretilir); **canlı 3D sahne** döndürülebilir ama telefonun ekran kartı 2-3 dakikalık hesabı 1/60 saniyede yapamadığı için fotogerçekçi olamaz. İkisini aynı anda vermenin tek yolu 24-36 açıyı önceden fotoğraflamak — grafik maliyetini 6-9 kat artırır.

## Karar
Gerilim **bölünerek** çözüldü:

1. **"3D" sekmesinde döndürülebilir Blender modeli görünür** (Blender sahnesinden dışa aktarılan model; paylaşılan referans görselindeki gibi). Anında açılır, parmakla döner.
2. **Fotogerçekçi render arka planda üretilir.** Hazır olunca **aynı ekranda** "Gerçekçi görünüm hazır" şeridi çıkar; dokununca tam ekran açılır. Ayrı bir sekme açılmaz.
3. **Ekran düzeni (yukarıdan aşağı)**:
   - Üst çubuk: geri + oda adı
   - **"Kat Planı | 3D" seçici** (bugünkü üçüncü sekme "Roomplan" kalkar)
   - **Büyük görüntü alanı** — ekranın yarısından biraz fazlası, tam genişlik
   - Tek satır ölçü şeridi (Alan · Boyutlar)
   - **Kısa not**: tek cümle, en fazla 110 karakter / 2 satır; **sistem yazısı (serif değil)**, 13 punto, gri; kutusuz ve çerçevesiz; sonunda "Detay" bağlantısıyla uzun açıklama alttan açılan panelde durur
   - Ürün başlığı satırı: "Bu tasarımdaki ürünler (6) · ₺48.500" + sağda "Tümünü Ekle"
   - **Ürün kutucukları**
   - **Alt sabit çubuk**: "AR ile Odanda Gör" (birincil) + "Yeniden Tasarla" (ikincil)
4. **"Kat Planı" = mobilyalı yerleşim planı** — duvarlar + kapı/pencere + yapay zekânın yerleştirdiği ürünler, dokununca ölçü etiketi. (Bugünkü kod zaten bunu yapıyor.)
5. **Sepete ekleme etkileşimi**: her kutucuğun sağ altında yuvarlak "+"; basınca hafif titreşim + "✓ Sepette" hâline döner ve tıklanamaz olur. Butonun hâli **sepetin gerçek içeriğinden** hesaplanır (çift ekleme koruması). "Tümünü Ekle" yalnız sepette olmayanları ekler ve sonucu tek satırda söyler. Alt sekmedeki Sepet ikonunda sayı rozeti. "Tasarımı Satın Al" ile "Tümünü Sepete Ekle" aynı işi yaptığı için **tek buton** olur ve ödeme yokken adı "Satın Al" olmaz.

## Gerekçe
- Kullanıcı ilk saniyeden itibaren odasını görür — 24 Temmuz'daki "anlık deneyim" ilkesi korunur.
- Fotogerçekçi kalite kaybolmaz, sadece ikinci adıma taşınır.
- Kurucunun "yazının fontu kötü ve çok yer kaplıyor" tespitinin gerçek nedeni konum değil, **biçim**: bugün açıklama Georgia serif 17 punto altın renkte ve kutu içinde — bu yüzden başlık gibi davranıyor. Başlık serif, not sans-serif olunca hiyerarşi düzelir.

## Değerlendirilen Alternatifler
- **Sadece fotogerçekçi fotoğraf**: hazır olana kadar ekranda gösterilecek hiçbir şey kalmaz; süre hiç ölçülmedi.
- **Parmakla döndürülebilen fotogerçekçi (döner tabla, 24-36 kare)**: her kare fotogerçekçi olur ama bekleme ve grafik maliyeti 6-9 kat artar, telefona inen dosya büyür. İleride bu ekrana eklenebilir — bugünkü karar o yolu kapatmıyor.
- **24 Temmuz kararının aynen kalması** (canlı sahne ana, fotoğraf ayrı yerde): "gösterilen şey gerçekçi olsun" isteğini karşılamıyordu.

## Sonuçlar (Consequences)
- [[2026-07-24 Anlık deneyim — canlı 3D sahne, render arka planda]] kararı **güncellendi**: ilke aynı, gösterilen model artık Blender sahnesinden geliyor ve fotoğraf aynı ekranda sunuluyor.
- Bugünkü "Roomplan" sekmesi kalkıyor; içeriği (canlı sahne) "3D" sekmesine taşınıyor.
- Referans görselindeki **ürün nokta işaretleri (hotspot)** için bugün veri üretilmiyor — Blender'ın her ürünün görüntüdeki konumunu da yazması gerekiyor. Küçük ama var olmayan bir iş → [[Open Questions]].
- Tasarım açıklaması iki ekranda iki farklı biçimde duruyor (sihirbaz sonucu / Projelerim); ikisi tek bileşene indirilecek.
- Yapay zekâdan ayrıca **tek cümlelik, en fazla 110 karakterlik özet** istenecek (uzun metni ortadan kesmek cümleyi bozar).

## Riskler
- Fotogerçekçilik beklenti tuzağı: görüntü ne kadar gerçekçi olursa kullanıcı onu o kadar "gerçek" sayar. Altında **ölçülmemiş** bir yerleşim (GPT-4o) ve **doğrulanmamış** model eşlemesi/ölçeği (Tripo) var.
- Backend hâlâ kurucunun Mac'inde; fotogerçekçi render Mac kapalıyken hiç üretilmez.

## İlgili Görevler
→ [[Task Board]]

## İlgili Bilgi
[[3D Render Pipeline]], [[30 Knowledge/Product/Product Flows|Product Flows (Knowledge)]]

## Kaynak Toplantı
[[2026 08 06 Thinking Session — Uygulama User Journey]]
