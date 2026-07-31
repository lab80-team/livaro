---
type: experiment
status: done
owner: "[[Selim]]"
created: 2026-07-29
related: []
---

# Kategori bazlı 3D üretim denemeleri — halı (Tripo vs düz yüzey) + kanepe kredi/kalite ölçümü

## Soru
İki ayrı soru, aynı araştırma turunda (2026-07-29 akşamı) test edildi:
1. Düz ürünlerde (halı) Tripo3D image/multiview-to-model mi, yoksa Tripo'suz düz yüzey + yüksek çözünürlüklü doku mu daha iyi sonuç veriyor?
2. Mobilyada Tripo3D'nin gerçek kredi maliyeti ve model sürümü/kalite ayarları arasındaki fark ne — dokümanın söylediğiyle Tripo'nun gerçekte faturaladığı aynı mı?

## Hipotez
- Sektör pratiği (Roomvo/Leap Tools patenti, Apple WWDC ince-nesne rehberi, ticari halı 3D varlıklarının 4-poligon spesifikasyonu) düz ürünlerin "yüzey detayı taşıdığını, uzamsal bilgi taşımadığını" söylüyor → halıda düz yüzey yolu Tripo'dan daha iyi/ucuz olmalı.
- Tripo'nun resmi fiyat dokümanı ile gerçek faturalanan kredi arasında sapma olabilir (kod incelemesinde `geometry_quality`'nin yalnızca v3.0+'da geçerli olduğu, P1 ailesinde ise hiç tanımlı olmadığı fark edildi — dokümantasyon parametre parametre tutarsız).

## Kurulum
**Halı testi:** Aynı Hereke halısı, aynı fotoğraf seti; bir tarafta gerçek Tripo `multiview_to_model` (`TRIPO3D_FAKE=0`, gerçek kredi), diğer tarafta kod tabanındaki Tripo'suz düz yüzey/GLB üreticisi (`src/three-d-pipeline/flat/`) ile üretim yapıldı, sonuçlar yan yana karşılaştırıldı.

**Kanepe testi:** Aynı kanepe, aynı fotoğraf seti; dört ayrı Tripo API çağrısı — model sürümü (`v3.1-20260211`, `v3.0-20250812`, `P1-20260311`) ve geometri/doku kalitesi (`standard`/`detailed`) kombinasyonları `TRIPO_MODEL_VERSION` / `TRIPO_GEOMETRY_QUALITY` / `TRIPO_TEXTURE_QUALITY` env değişkenleriyle tek tek denendi (bkz. `src/three-d-pipeline/tripo3d/tripo3d.service.ts` — bu üç ayar özellikle bu yan yana testi yapabilmek için env'den ayarlanabilir yapıldı). Tripo'nun görev bitiminde döndürdüğü `consumed_credit` alanı loglandı — **tahmin değil, ölçüm**.

## Sonuç

### Halı: düz yüzey kazandı
Aynı halı, iki yöntemle üretilip yan yana incelendi: düz yüzey + yüksek çözünürlüklü doku yolunda desen fotoğraf kadar net; Tripo çıktısında desen bulanık. Ayrıca maliyet: düz yüzey **0 kredi**, Tripo **~50-70 kredi**. İki yönde de düz yüzey kazandı (kalite + maliyet).

### Kanepe: gerçek Tripo kredi tablosu

| Ayar | Bildirilen kredi | Üçgen sayısı | Doku | Dosya boyutu |
|---|---|---|---|---|
| v3.1, standart geometri + standart doku | 30 | 1.378.939 | 2K | **38,7 MB — kullanılamaz** |
| v3.1, detaylı geometri + detaylı doku | 60 | 4.683 | 4K | 4,5 MB |
| v3.0, detaylı geometri + detaylı doku | 60 | 4.815 | 4K | 4,9 MB |
| P1 (en yeni aile), detaylı doku | **60** (dokümanda "50, ek ücret yok" yazıyor) | 4.735 | 4K | 4,9 MB |

**Kritik bulgular:**
1. **"Ucuz" ayar bir tuzak.** 30 kredilik standart ayar 1,4 milyon üçgen + 38,7 MB üretiyor — telefonda/AR'da fiilen kullanılamaz. +20 kredilik "detaylı geometri" (Ultra Mode) üçgen sayısını 1,4 milyondan ~4.700'e indiriyor; yani o ek kredi, modeli KULLANILABİLİR kılan şeyin ta kendisi — süs değil.
2. **Tripo'nun kendi dokümanı yanlış.** P1 ailesi için doküman "her şey dahil 50 kredi, ek parametre sürşarjı yok" diyor (`docs.tripo3d.ai/get-started/pricing.html`); gerçekte **60 kredi** faturalandı.
3. **Üç pahalı seçenek teknik olarak birbirine çok yakın.** v3.1-detaylı, v3.0-detaylı ve P1-detaylı aynı fiyatta (60 kredi), benzer üçgen sayısı ve doku boyutunda — aralarındaki seçim artık teknik değil, görsel/üslup tercihi.

### 8K doku YOK
Üç bağımsız kanıtla doğrulandı: (a) Tripo API'sinde 8K için parametre yok; (b) `texture_quality: 'detailed'`'ın dokümandaki tanımı zaten "4K'ya yükselt"; (c) Tripo'nun kendi dönüştürücüsünde çözünürlük tavanı 4096. Ayrıca istesek de bize yaramazdı: Apple'ın AR Quick Look tavsiyesi 2048×2048 dokudur; biz zaten 4096 gönderiyoruz — önerilenin 4 katı bellek.

## İşe Yarayan
- Halıda düz yüzey yolu: kalite + maliyet ikisinde de net kazanan.
- `consumed_credit` loglaması: tahmin yerine ölçüm — dokümandaki hatayı (P1 fiyatı) bu sayede yakaladık.

## Başarısız Olan
- Tripo'nun "standart" (30 kredi) ayarı kanepede fiilen kullanılamaz çıktı üretti (38,7 MB, 1,4M üçgen) — dokümanın "ucuz seçenek" izlenimi yanıltıcı.

## Kısıtlar (Limitations)
- Halı testinde kullanılan 4 fotoğraf gerçek 4 açı değildi (biri düz üstten katalog çekimi, biri zeminde açılı çekim) — halı zaten düz bir ürün olduğu için yan açı kavramı anlamsız, ama bu yüzden ön/arka/sol/sağ → Tripo front/left/back/right eşlemesinin doğruluğu bu testte **ölçülemedi** (ayrı açık soru, bkz. [[Open Questions]]).
- Tek kanepe, tek fotoğraf seti üzerinden dört ayar denendi — farklı mobilya tipi/karmaşıklığında sonuç değişebilir (**Needs Validation**).

## Karar / Sonuç
→ [[2026-07-29 Kategori bazlı 3D üretim stratejisi — halı düz yüzey, mobilya Tripo devam, perde sonraya]]

## İlgili Kod / Branch
`src/three-d-pipeline/flat/` (düz yüzey üreticisi), `src/three-d-pipeline/tripo3d/tripo3d.service.ts` (model sürümü/kalite env parametreleri + kredi logu), commit'ler `f027673`, `4619feb`, `d460535` (dal `feature/store-web`, main'e `44a4497` ile merge edildi).

## İlgili Kaynak
[[2026-07-31 Kategori 3D Stratejisi, Tripo Kredi Ölçümü, iOS Doku Düzeltmesi ve Main Merge]]
