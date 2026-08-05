---
type: decision
status: accepted
created: 2026-08-05
source: "[[2026-08-06 Halı Doku Delikleri, Saçak Modeli ve Migration Kurtarması]]"
related: ["[[2026-07-29 Kategori bazlı 3D üretim stratejisi — halı düz yüzey, mobilya Tripo devam, perde sonraya]]", "[[2026-08-06 Düz üründe fotoğraf boşluğu zorunlu — birebir kırpım istisna]]", "[[Seller Experience]]", "[[Known Pitfalls]]"]
---

# Halı ölçüsü saçak hariç — saçak ayrı yassı şerit olarak modellenir

## Bağlam

Halının 3D dokusundaki delik kusuru düzeltilince püskül ilk kez dokuda görünür oldu. Ama doku halı + saçağı birlikte içerdiği hâlde model kutusu satıcının girdiği ölçüde kalıyordu; yani saçak ürünün ölçüsünün İÇİNE sıkıştırılıyor ve halının deseni boyuna **~%11 eziliyordu**. Kod bunu fark edip uyarı basıyor ama düzeltmiyordu.

Doğru davranış, satıcının girdiği en/boy ölçüsünün saçağı **içerip içermediğine** bağlıydı — bu ölçülebilir bir şey değil, bir tanım kararı. Kurucuya soruldu.

## Karar

1. **Satıcının girdiği en/boy ölçüsü SAÇAK HARİÇTİR** — halının dokuma alanıdır.
2. **Saçak, ürünün ölçüsünün DIŞINA, ayrı yassı şerit olarak modellenir.** Halının kalınlığında blok değil: saçak hav değil çözgü ipliğidir, yerde düz durur.
3. Modelin gerçek dış ölçüsü (saçak dahil) **ürünün nominal ölçüsünden ayrı bir alan olarak taşınır**; modeli gösteren taraf ölçeklemeyi buna göre yapar.

## Gerekçe

- Türkiye'de halı ölçüsü zaten saçak hariç verilir; satıcının alışkanlığına ters düşmemek gerekiyor.
- Saçağı ölçünün içine saymak halının **desenini eziyor** — ölçülen sapma tipik olarak %5-12. Bu sessiz bir kalite kaybı: satıcı da müşteri de "halı biraz basık" der ama sebebini bulamaz.
- Saçağı halının kalınlığında bir blok olarak modellemek onu 8 mm'lik bir duvar gibi gösterirdi. Sektörün ticari halı varlıklarında saçak ayrı yassı şerittir.

## Değerlendirilen Alternatifler

- **Ölçüyü saçak dahil saymak** (bugünkü davranışı meşrulaştırmak): kod değişikliği gerektirmezdi ama satıcının gerçekte girdiği sayıyla çelişirdi ve deseni ezmeye devam ederdi. Kurucu reddetti.
- **Saçağı hiç modellememek** (dokudan da kırpmak): en basit yol, ama püskül halının görsel kimliğinin parçası ve kurucu açıkça "püskülü modelleyelim" dedi.

## Sonuçlar (Consequences)

- Gövde/saçak ayrımı **geometrik** yapılıyor (`solidBodyRect`): halı gövdesinin her satırı baştan sona dolu, saçak bandının satırları tel/boşluk sırası olduğu için yarı dolu. Renk varsayımı yok, saçağın hangi kenarda olduğu varsayımı yok.
- Oran düzeltmesi artık **gövdeye** bakıyor (eskiden kadrajın tamamına bakıyordu ve saçağı halının ölçüsü sanıyordu).
- Zincirin tamamı değişti: geometri → veritabanı (`ThreeDModel.model{Width,Height,Depth}Cm`, nullable) → API → iOS. **iOS'ta değişiklik şarttı**: `ModelLoader` modeli ürünün nominal kutusuna zorluyordu, yani saçağı geri sıkıştırırdı. Artık model kendi gerçek ölçüsünü bildiriyorsa ona göre ölçekleniyor; bildirmiyorsa (Tripo yolu, eski kayıtlar) eski davranış aynen sürüyor.
- Ölçülen sonuç (207×300 cm halı): gövde birebir girilen ölçüde, saçak payı 13,8 + 12,5 cm dışarıda, model toplam 312,3 cm boyunda, saçak yassı. Maliyet 12 → 16 üçgen.
- Satıcı panelindeki halı rehberine "en/boy ölçüsünü **saçak hariç** verin" notu eklendi.

## Riskler

- **Eğik çekimde saçak ayrımı yapılmıyor** — perspektif düzeltme yolunda halının dört köşesi saçak uçlarından ölçüldüğü için gövde sınırı güvenilir değil. Gerileme değil (eskiden hiç yoktu) ve dik tepeden çekim zaten şart koşuluyor; kodda ve testte açıkça işaretli. Codex incelemesi bu turda bırakılmasına katıldı.
- Kısa ve yoğun dokunmuş püskülü olan halılarda ayrım **tetiklenmiyor** (bant %90'dan fazla dolu olduğu için "hepsi gövde" sayılıyor). Ölçülen bir örnekte püskül halının boyunun %0,7'siydi (~2 cm) — bu durumda doğru davranış zaten ayırmamak.
- Model ölçüsü alanları nullable; Tripo yolu bunları **koşulsuz null yazıyor** ki kategori halıdan mobilyaya çevrilip yeniden üretilince bayat halı ölçüsü kalmasın (Codex bulgusu).

## İlgili Görevler

- Gerçek cihazda AR doğrulaması (bkz. [[Task Board]]).
- Perde tedarik yolu seçilince saçak/kıvrım modellemesi bu kararla birlikte gözden geçirilmeli.

## İlgili Bilgi

[[Seller Experience]] · [[3D Render Pipeline]] · [[Known Pitfalls]]

## Kaynak Toplantı

Bu bir toplantı kararı değil — 5-6 Ağustos Claude oturumunda, ölçüm sonuçları kurucuya sunulup doğrudan soruldu, kurucu karar verdi. Kayıt: [[2026-08-06 Halı Doku Delikleri, Saçak Modeli ve Migration Kurtarması]].
