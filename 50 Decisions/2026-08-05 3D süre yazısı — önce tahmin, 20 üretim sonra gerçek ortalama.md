---
type: decision
status: accepted
created: 2026-08-05
source: "[[2026 08 05 Thinking Session — Mağaza Paneli 3D İlerleme ve Stok Göstergesi]]"
related: ["[[2026-08-05 3D ilerleme göstergesi — her sayfada kapatılabilir kutucuk]]"]
---

# 3D süre yazısı — önce tahmin, 20 üretim sonra gerçek ortalama

## Bağlam
Kurucu, 3D üretimi sırasında mağazaya **ortalama kaç dakikada biteceğinin** yazılmasını istedi. Ama bu sayı elimizde yok: 3D üretiminin ne kadar sürdüğü hiç ölçülmemiş ve geriye dönük de çıkarılamıyor, çünkü 3D kaydı her denemede öncekinin üstüne yazılıyor. Elimizdeki tek somut sayı bir **tavan**: arka plandaki işçi Tripo'yu en fazla 5 dakika bekliyor (60 sorgu × 5 saniye), aşarsa "zaman aşımı" deyip başarısız sayıyor.

## Karar
İki aşamalı:
1. **İlk sürüm:** ekranda ve kutucukta "genelde birkaç dakika sürer" yazar. Sayı verilmez.
2. **Aynı anda** her 3D denemesinin başlama ve bitme saati kaydedilmeye başlanır. **20 gerçek üretim birikince** ekran kendiliğinden "ortalama X dakika"ya döner.

Sıra bekleyen ürünlerde süre sözü verilmez — orada "sırada bekliyor" yazar (bkz. [[2026-08-05 3D ilerleme göstergesi — her sayfada kapatılabilir kutucuk]]).

## Gerekçe
Kurucunun istediği sayı ancak kendi verimizden çıkarsa gerçek olur. Bugün yazılacak her dakika tahmindir ve tutmadığı ilk seferde mağaza sahibinin güvenini doğrudan vurur — üstelik yüzde göstergesi bu tutarsızlığı görünür kılacağı için etki bugünkünden daha sert olur. İki aşamalı yol isteği reddetmiyor, bir-iki hafta erteliyor.

## Değerlendirilen Alternatifler
- **Şimdiden bir sayı yaz (ör. "yaklaşık 4 dakika")** — reddedildi: uydurma olur.
- **"Genelde 5 dakikadan kısa sürer"** — PM A'nın ilk önerisi, kendisi geri çekti: 5 dakika sistemin **başarısızlık eşiği**, tipik süre değil; söz gibi görünen bir uyarı olurdu.
- **Hiç süre yazma** — PM B'nin ilk önerisi, kendisi geri çekti: kurucunun açık isteğini reddetmek olurdu.

## Sonuçlar (Consequences)
- Her 3D denemesinin başlama/bitme saati kaydedilecek — bugün böyle bir kayıt yok (3D satırı her denemede üzerine yazılıyor, yani denemeler ayrı ayrı saklanmalı).
- Ölçüm biriktikçe **5 dakikalık kesme sınırının gerçek sürelerin üstünde mi altında mı olduğu** ilk kez görülecek. Altındaysa bugün sessizce başarısız olan üretimler var demektir.
- Ekrandaki metin veri birikince kendiliğinden değişecek — ayrı bir sürüm çıkarmaya gerek kalmayacak.

## Riskler
- Kategoriler arası süre farkı büyükse (mobilya Tripo'dan geçiyor, halı geçmiyor) tek bir ortalama yanıltabilir. Kategoriye göre ayrı sayılıp sayılmayacağı **To Be Decided** → [[Open Questions]].
- 20 üretim eşiği kurucu tarafından değil bu oturumda önerildi ve kabul edildi; ilk gerçek verilerle değişebilir.

## İlgili Görevler
- 3D üretim sürelerini ölçmeye başla → [[Task Board]]

## İlgili Bilgi
- [[Seller Experience]], [[3D Render Pipeline]], [[Known Pitfalls]]

## Kaynak Toplantı
- [[2026 08 05 Thinking Session — Mağaza Paneli 3D İlerleme ve Stok Göstergesi]] (soru 1)
