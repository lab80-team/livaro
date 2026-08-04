---
type: decision
status: accepted
created: 2026-08-04
source: "[[2026 08 04 Thinking Session — Admin Paneli]]"
related: ["[[Admin Panel]]", "[[2026-08-04 PM Tartışması — Admin Paneli]]"]
---

# Admin panel v1 kapsamı — kuyruk ana sayfa, mağaza kartları, ciro/reklam alanları yok

## Bağlam
Mevcut admin sitesi kasıtlı asgari (Başvurular / Ürün Onayı / Takılanlar). Kurucu kapsamlı paneli tarif etti; iki PM'li tartışma sonrası kapsam netleşti. Ödeme sistemi ve reklam ürünü henüz olmadığı için ciro/satış/reklam verisi üretilmiyor.

## Karar
1. **Giriş (ana) sayfası pilotta = iş kuyruğu**: 4 bekleyen sayacı (başvuru, ürün onayı, takılan 3D, düzenleme onayı) + son kaydolan mağaza ve kullanıcı listeleri. **Sütun/çizgi grafikler veri birikince eklenir** (vizyon korunuyor: günlük kullanıcı kaydı, satış vb.).
2. **Mağazalar sekmesi** (sol menüde): kart görünümü — logo, isim, açıklama, ürün sayısı, yayınlanmış 3D sayısı, kayıt tarihi. Kartın sağ üstünde **kırmızı bildirim rozeti**; rozete **üç bekleyen iş türü de sayılır**: bekleyen ürün onayı + takılan 3D (STUCK) + düzenleme onayı. Karta tıklayınca mağaza detayı.
3. **Ürünler sekmesi**: tüm ürünler; durum, stok, 3D durumu görünür.
4. **Ciro, satış ve reklam alanları şimdilik hiç konmaz** — ciro/satış ödeme kuruluşu seçilip checkout çalışınca, reklam sayıları "Sponsorlu" ürünü inşa edilince eklenir. Boş kolon taşınmaz.
5. **Mağaza sayısı göstergesi = kayıt olan (başvuran) toplam**, onaylı/bekleyen/reddedilen ayrımıyla.
6. Mevcut üç ekran (Başvurular, Ürün Onayı, Takılanlar) kalır; yanlarına bekleyen sayaçları eklenir.

## Gerekçe
Az veriyle grafik hem anlamsız hem yanıltıcı ("veri yok" ile "ürün tutmuyor" aynı görünür); panelin bugünkü işi kuyruk eritmek. Boş ciro/reklam kolonları paneli bozuk gösterir; veri doğunca eklemek kolay, geçmişe dönük kayıp yok.

## Değerlendirilen Alternatifler
- Grafiklerin ilk günden konması (kurucunun ilk isteği) — iki PM'in "boş dashboard moral bozar + panele bakma alışkanlığını öldürür" itirazıyla veri birikme sonrasına ertelendi.
- Ciro/reklam kutularının "yeri hazır" boş durması — reddedildi.

## Sonuçlar (Consequences)
- Grafik altyapısı v1'de kurulmaz; tasarım vizyonu (sütun/çizgi) [[Admin Panel]] notunda saklı.
- Rozet üç kuyruğun toplamını gösterdiği için mağaza detayında tür bazlı dökümün görünmesi gerekir.

## Riskler
- Grafiklerin "veri birikince" eşiği tanımsız — ne zaman ekleneceği yoruma açık.

## İlgili Görevler
Yok (inşa zamanlaması açık → [[Open Questions]]).

## İlgili Bilgi
[[Admin Panel]], [[Seller Experience]], [[Marketplace Model]]

## Kaynak Toplantı
[[2026 08 04 Thinking Session — Admin Paneli]]
