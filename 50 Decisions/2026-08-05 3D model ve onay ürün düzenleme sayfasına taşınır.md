---
type: decision
status: accepted
created: 2026-08-05
source: "[[2026 08 05 Thinking Session — Mağaza Paneli 3D İlerleme ve Stok Göstergesi]]"
related: ["[[2026-08-05 3D ilerleme göstergesi — her sayfada kapatılabilir kutucuk]]"]
---

# 3D model ve onay ürün düzenleme sayfasına taşınır

## Bağlam
Kurucu "ürünü düzenlemeye basınca 3D model daha aşağıda gözükmeli" dedi. Bugünkü durum:
- Ürün düzenleme sayfasında **3D model hiç görünmüyor**.
- Modeli görmek için ayrı bir "3D'yi İncele" sayfasına gitmek gerekiyor ve o sayfa **yalnız "mağaza 3D onayı bekleniyor" durumundaki** ürünlerde açılıyor. Yani onaylanmış veya yayındaki bir ürünün modeline mağaza sahibi hiçbir yerden bakamıyor.
- Onayla/Reddet düğmeleri o ayrı sayfada.

## Karar
Ayrı "3D'yi İncele" sayfası **kaldırılır**. Hem 3D modelin döndürülerek incelenmesi hem de **Onayla / Reddet** düğmeleri ürün düzenleme sayfasının altına taşınır. Model, üretildikten sonra ürünün her durumunda burada görünür.

İlerleme kutucuğu iş bitince "3D modeliniz hazır — inceleyin" bağlantısına dönüşür ve doğrudan buraya götürür → [[2026-08-05 3D ilerleme göstergesi — her sayfada kapatılabilir kutucuk]].

## Gerekçe
Aynı işi iki ayrı yerde yapmak onayın nerede verildiğini bulanıklaştırıyor ve ürünlerin "mağaza onayı bekliyor"da takılı kalmasının başlıca sebeplerinden biri. Tek yerde toplanınca mağaza sahibi modeli her zaman bulabilir, kurucunun isteği de karşılanır.

## Değerlendirilen Alternatifler
- **Model düzenleme sayfasında görünsün ama sadece bakmalık; Onayla/Reddet ayrı sayfada kalsın** (PM B) — kurucu tarafından reddedildi. PM B'nin itirazı kayıtlıdır (aşağıda, Riskler).
- **İkisi de kalsın** — reddedildi: iki PM de onayın iki yerde olmasını sakıncalı buldu.

## Sonuçlar (Consequences)
- Düzenleme sayfası uzayacak: form alanları + fotoğraf slotları + 3D model + onay düğmeleri.
- 3D üretildikten sonra kategori ve ölçüler zaten kilitli (model o bilgilerle üretildiği için); bu kural değişmiyor.
- "3D'yi İncele" düğmesi ürün listesinden kalkacak, yerine düzenleme sayfasına yönlendiren tek yol kalacak.

## Riskler
- **PM B'nin kayıtlı itirazı:** reddetmek geri alınamaz (bir deneme hakkı yanıyor ve bugünkü kuralla mağaza aynı fotoğraflarla tekrar deneyemiyor). Bu düğmeleri, yanında "Bilgileri Güncelle" düğmesi olan uzun bir formun altına koymak **yanlış tıklama** üretebilir. Tasarımda ayrı bir bölüm başlığı, görsel ayrım ve reddetmede onay sorusu gerekiyor.
- Reddetmenin geri alınamazlığı, [[2026-08-05 Sistem hatasında 3D deneme hakkı iade edilir]] kararıyla kısmen hafifliyor — ama o karar yalnız **sistem** hatasını kapsıyor, mağazanın kendi reddini değil.

## İlgili Görevler
- 3D modeli ve Onayla/Reddet'i ürün düzenleme sayfasına taşı, ayrı sayfayı kaldır → [[Task Board]]

## İlgili Bilgi
- [[Seller Experience]]

## Kaynak Toplantı
- [[2026 08 05 Thinking Session — Mağaza Paneli 3D İlerleme ve Stok Göstergesi]] (soru 7)
