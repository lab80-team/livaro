---
type: decision
status: accepted
created: 2026-07-29
source: "[[2026-07-31 Kategori 3D Stratejisi, Tripo Kredi Ölçümü, iOS Doku Düzeltmesi ve Main Merge]]"
related: ["[[Kategori bazlı 3D üretim denemeleri — halı Tripo vs düz yüzey, kanepe kredi-kalite ölçümü]]", "[[Seller Experience]]", "[[2026-07-29 3D üretimi 4 açının tamamını kullanır — Tripo multiview_to_model]]"]
---

# Kategori bazlı 3D üretim stratejisi (halı düz yüzey, mobilya Tripo devam, perde sonraya)

## Bağlam
Mağaza web sitesi build'inin ardından (2026-07-29 akşamı) üç kollu bir araştırma yapıldı: Tripo'nun resmi API dokümanı, sektör pratiği (Roomvo/Leap Tools patenti, Apple WWDC ince-nesne rehberi, ticari halı 3D varlıklarının 4-poligon spesifikasyonu) ve kendi kodumuzun incelenmesi. Ortaya çıkan soru: her ürün kategorisi için (halı, mobilya, perde) aynı 3D üretim yöntemi (Tripo image/multiview-to-model) doğru mu?

Sektör pratiği, düz ürünlerin (halı, perde) "yüzey detayı taşıdığını, uzamsal bilgi taşımadığını" söylüyor — yani bunlar için genel amaçlı image-to-3D yanlış araç olabilir. Bu hipotez, gerçek bir yan yana denemeyle test edildi → [[Kategori bazlı 3D üretim denemeleri — halı Tripo vs düz yüzey, kanepe kredi-kalite ölçümü]].

Kurucuya soruldu; kurucu karar verdi.

## Karar
Kategoriye göre üç farklı 3D üretim yolu:

1. **Halı: Tripo KULLANILMAYACAK.** Düz yüzey + yüksek çözünürlüklü doku (`src/three-d-pipeline/flat/`).
2. **Mobilya: Tripo3D multiview devam** (`multiview_to_model`, 4 açı — bkz. [[2026-07-29 3D üretimi 4 açının tamamını kullanır — Tripo multiview_to_model]]). Model sürümü v2.5'ten (dokümana hiç `model_version` gönderilmiyordu, Tripo sessizce Ocak 2025 varsayılanına düşüyordu) v3.1'e (`v3.1-20260211`) çekildi.
3. **Perde: SONRAYA BIRAKILDI.** Tedarik yolu seçilmedi (aşağıda detay).

## Gerekçe
- **Halı:** Aynı Hereke halısı hem Tripo hem düz yüzeyle üretilip yan yana karşılaştırıldı — düz yüzeyde desen fotoğraf kadar net, Tripo'da bulanık; ayrıca maliyet 0 kredi vs ~50-70 kredi. Kalite VE maliyet ikisinde de düz yüzey kazandı; kanıt olmadan geçilmedi ("önce kanıtla, sonra geç" ön-şartı karşılandı).
- **Mobilya:** v3.1 sürüm notu "ince detay + karmaşık desen belirgin daha net" diyor (ahşap dokusu, kumaş dokuması, marka yazısı — mobilyada doğrudan işimize yarayan fark), baz fiyat v2.5 ile aynı (kredi artışı yok).
- **Perde:** Perdenin şekli ÜRÜNÜN değil ODANIN özelliği (korniş yüksekliği, pencere genişliği, bolluk/pile miktarı) — tek bir ürün fotoğrafından image-to-3D ile üretmek kavramsal olarak yanlış. Sektör 8-15 hazır kıvrımlı mesh tutup üründen yalnızca kumaşı giydiriyor.

## Değerlendirilen Alternatifler
- Halıyı da Tripo ile üretmeye devam etmek (tutarlılık gerekçesiyle) — kanıt karşısında reddedildi.
- Perde için hemen hazır kıvrımlı model kütüphanesi kurmaya başlamak — araştırıldı (`~/Desktop/livaro/.superpowers/sdd/perde-3d-varlik-arastirmasi.md`) ama tedarik yolu belirsizliği nedeniyle ertelendi (aşağıya bakın).

## Sonuçlar (Consequences)
- Halı yolu **uygulandı ve devrede**: `src/three-d-pipeline/flat/` (düz yüzey/GLB üreticisi), web/admin'de halı seçilince tek "tepeden" fotoğraf slotu + halıya özel çekim rehberi.
- Mobilya yolunda gerçek kredi maliyeti ölçüldü (dokümanın söylediğinden farklı çıktı) → [[Kategori bazlı 3D üretim denemeleri — halı Tripo vs düz yüzey, kanepe kredi-kalite ölçümü]].
- [[Seller Experience]] ve [[Current State]] güncellendi.

## Riskler
- **Perde tedarik yolu seçilmedi — açık.** Araştırma notu (`.superpowers/sdd/perde-3d-varlik-arastirmasi.md`) şunları buldu: 10 modellik başlangıç seti önerisi; freelancer $500-1500 / 3-5 hafta; lisanslar uygun görünüyor ama "kumaş değiştirilebilir UV" (satın almadan bilinemez) asıl risk; tül perdede RealityKit saydamlık sıralama riski. Hangi tedarik yolunun seçileceği → [[Open Questions]].
- **Mobilyada ön/arka/sol/sağ → Tripo front/left/back/right eşlemesi hâlâ doğrulanmadı** — halı testi bunu ölçemedi (halı düz bir ürün, yan açı kavramı anlamsız; kullanılan 4 fotoğraf da gerçek 4 açı değildi). Gerçek bir mobilyanın 4 gerçek açısıyla ayrı bir doğrulama gerekiyor → [[Open Questions]].
- Kanepe kredi testi tek ürün/tek fotoğraf seti üzerinden yapıldı — genellenebilirliği **Needs Validation**.

## Kaynak Toplantı
Bu bir toplantı kararı değil — mağaza web sitesi build oturumunun devamında (2026-07-29 akşamı), üç kollu araştırma + gerçek Tripo denemesi üzerine kurucuya doğrudan soruldu, kurucu karar verdi. Kayıt: [[2026-07-31 Kategori 3D Stratejisi, Tripo Kredi Ölçümü, iOS Doku Düzeltmesi ve Main Merge]] (kod reposu ayrıntısı: `.superpowers/sdd/progress.md`, "KATEGORİ BAZLI 3D STRATEJİSİ" bölümü).
