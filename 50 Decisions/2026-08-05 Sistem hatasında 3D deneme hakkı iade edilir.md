---
type: decision
status: accepted
created: 2026-08-05
source: "[[2026 08 05 Thinking Session — Mağaza Paneli 3D İlerleme ve Stok Göstergesi]]"
related: ["[[2026-07-28 Ürün yükleme ve panel — 3D zorunlu, Tripo 2 hak]]"]
---

# Sistem hatasında 3D deneme hakkı iade edilir

## Bağlam
Ürün başına 2 Tripo deneme hakkı kuralı 2026-07-28'de kondu → [[2026-07-28 Ürün yükleme ve panel — 3D zorunlu, Tripo 2 hak]]. Bu oturumda kodda ölçülen davranış şu:
- Deneme hakkı **gönderim anında** düşüyor, sonucuna bakılmadan.
- Aynı fotoğraf setiyle tekrar gönderim koda gömülü şekilde yasak (fotoğrafların parmak izi `lastImageSetHash` olarak saklanıyor, eşleşirse istek reddediliyor).
- Başarısızlıkta hak iadesi yok.
- Arka plandaki işçi Tripo'yu en fazla 5 dakika bekliyor; aşarsa "zaman aşımı" deyip işi başarısız sayıyor.

Sonuç: sistem kendi hatasıyla (zaman aşımı, çökme, dağıtım sırasında işin düşmesi) patladığında **hatası olmayan mağaza hem hakkını yakıyor hem de aynı fotoğrafları yeniden gönderemiyor** — yeni fotoğraf çekmek zorunda kalıyor. Bugün bu haksızlık görünmüyor çünkü mağaza zaten ne olduğunu bilmiyor; ilerleme yüzdesi eklenince görünür hâle gelecek.

## Karar
Sistem kendi hatasıyla başarısız olursa (Tripo zaman aşımı, çökme, kuyruk hatası):
- **Deneme hakkı geri verilir.**
- Mağaza **aynı fotoğraflarla** tekrar deneyebilir.

Mağaza kaynaklı ret (mağaza modeli beğenmeyip "Reddet" demesi) bu kuralın dışındadır — orada hak yanmaya devam eder ve yeni fotoğraf gerekir.

## Gerekçe
İki PM de bunu birinci öncelikli düzeltme saydı. Yüzde ekranı bu haksızlığı gizli hâlden görünür hâle getireceği için önce bunun düzelmesi gerekiyor: mağaza "%78'e geldi, sonra sistem yedi, üstelik hakkımı da aldı" dediğinde destek yükü doğrudan kuruculara döner. Kendi hatamızın bedelini satıcıya ödetmek, henüz tek bir gerçek satıcının bile kullanmadığı bir panelde en pahalı ilk izlenim olur.

## Değerlendirilen Alternatifler
- **Hak iade edilsin ama yine yeni fotoğraf istensin** — reddedildi: mağaza yine cezalandırılmış olur, sadece daha az.
- **Bugünkü gibi kalsın** — reddedildi.

## Sonuçlar (Consequences)
- Başarısızlığın **kimden kaynaklandığı** ayırt edilmeli: sistem hatası mı, mağaza reddi mi. Bugün bu ayrım kodda net değil.
- Aynı fotoğraf setiyle tekrar gönderim engeli, "önceki deneme sistem hatasıyla bitti" durumunda **atlanabilir** olmalı.
- Her yeniden deneme gerçek Tripo kredisi yakar (kullanılabilir kalite ürün başına 60 kredi) — sistem hatasında iade, maliyeti bize bırakır. Bu bilinçli bir tercihtir.
- Kutucuktaki hata mesajı buna göre yazılır: hak kaldıysa "Olmadı — 1 hakkınız kaldı, tekrar deneyin" → [[2026-08-05 3D ilerleme göstergesi — her sayfada kapatılabilir kutucuk]].

## Riskler
- Sürekli zaman aşımına düşen bir ürün, hak iadesi sayesinde sonsuz döngüye girip kredi yakabilir. Bir üst sınır (ör. sistem hatası kaynaklı iade sayısı) gerekip gerekmediği **To Be Decided**.
- 5 dakikalık kesme sınırının gerçek sürelerin altında olup olmadığı hâlâ bilinmiyor; altındaysa iade kuralı sık tetiklenir. Ölçüm bunu gösterecek → [[2026-08-05 3D süre yazısı — önce tahmin, 20 üretim sonra gerçek ortalama]].

## İlgili Görevler
- Sistem hatasında deneme hakkını iade et, aynı fotoğraflarla tekrar denemeye izin ver → [[Task Board]]

## İlgili Bilgi
- [[Seller Experience]], [[Known Pitfalls]]

## Kaynak Toplantı
- [[2026 08 05 Thinking Session — Mağaza Paneli 3D İlerleme ve Stok Göstergesi]] (soru 3)
