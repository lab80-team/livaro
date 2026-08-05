---
type: decision
status: accepted
created: 2026-08-05
source: "[[2026-08-05 Build Oturumu — Admin Paneli Dilim 1]]"
related: ["[[Admin Panel]]", "[[2026-08-04 Ürün düzenlemede yeniden onay — yalnız vitrin alanları]]"]
---

# Yeniden onay davranışı — ürün yayında kalır, geri yazmak öneriyi iptal eder

## Bağlam

4 Ağustos kararı yeniden onayın **hangi alanlarda** olacağını söylüyordu (foto/başlık/açıklama; stok ve fiyat değil) ama iki davranış sorusunu açık bırakmıştı: onay beklerken müşteri ne görür, ve mağaza fikrini değiştirirse ne olur?

İkincisi inşa sırasında ortaya çıktı: kod incelemesi somut bir **sessiz yanlış veri** yolu gösterdi.

## Karar

**1. Onay beklerken ürün YAYINDA kalır.** Müşteri ürünün onaylı **eski** halini görmeye devam eder; yeni hali ancak admin onaylayınca yayına geçer. Değişiklik ürünün kendisine değil ayrı bir "bekleyen düzenleme" kaydına yazılır.

**2. Vitrin alanını eski değerine geri yazmak, o alanın bekleyen önerisini İPTAL eder.** Geriye hiç öneri kalmazsa bekleyen kayıt tamamen kapanır (fotoğrafları da depodan silinir).

## Gerekçe

**1. için:** mağaza satış kaybetmemeli. Başlıktaki bir yazım hatasını düzelten mağaza, admin onaylayana kadar satışını durdurmuş olmamalı. Denetimden kaçış da yok — müşterinin gördüğü yüz hep onaylanmış olan.

**2. için:** kararın kaynağı somut bir hata senaryosuydu. Ürünün adı "Koltuk A"; mağaza "Koltuk B" yapıp kaydediyor (onaya düşüyor); sonra vazgeçip adı "Koltuk A"ya geri yazıyor. Panel "onaya giden bir şey yok" diyor **ama bekleyen kayıtta hâlâ "Koltuk B" duruyor** — admin onaylayınca ürün, mağazanın açıkça geri aldığı ada dönüyor.

Kurucuya üç seçenek sunuldu; "o alanın önerisi iptal olsun" seçildi çünkü en sezgisel davranış bu: **ekranda ne yazıyorsa onaya giden o.**

## Değerlendirilen Alternatifler

**1. için:**
- Ürün onaylanana kadar yayından insin — en basit çözüm; ama başlıkta bir harf düzelten mağaza satışını durdurmuş olurdu. Reddedildi.
- Yeni hali hemen yayında, onay sonradan — onaylanmamış içerik bir süre yayında kalırdı. Reddedildi.

**2. için:**
- Panelde uyarı göster, öneri kalsın — sessizlik ortadan kalkardı ama mağaza tek alanı geri almak için yine her şeyi geri çekmek zorunda kalırdı. Reddedildi.
- Olduğu gibi bırak — panelin söylediği ile gerçeğin örtüşmediği durum sürerdi. Reddedildi.

## Sonuçlar (Consequences)

- Ürün başına en fazla **bir** bekleyen düzenleme kaydı olur; mağaza tekrar düzenlerse aynı kayıt güncellenir.
- Mağaza paneli, bekleyen kayıt varken formu **öneriyle** doldurur ki geri yazma bilinçli bir eylem olsun. Reddedilmiş kayıtta bu yapılmaz — yapılsaydı ilgisiz bir kayıt öneriyi yeniden onaya sokup **adminin red notunu silerdi**.
- Reddedilen kayıt silinmez; `REJECTED` + nedeniyle kalır, mağaza görüp kapatınca silinir.
- Yanıtta hangi alanın nereye gittiği bildiriliyor ("Fiyat güncellendi. Ad değişikliğiniz onaya gönderildi."), iptal edilenler de ayrıca.

## Riskler

- Saf iptal sonrası kayıt, artık geçerli olmayan bir red notuyla `REJECTED` kalabiliyor. Kilit değil (yeni öneri gönderilince `PENDING`'e döner, ya da geri çekilir) ve panel mağazaya ne yapacağını söylüyor.

## İlgili Bilgi

[[Admin Panel]], [[Seller Experience]]

## Kaynak

[[2026-08-05 Build Oturumu — Admin Paneli Dilim 1]]
