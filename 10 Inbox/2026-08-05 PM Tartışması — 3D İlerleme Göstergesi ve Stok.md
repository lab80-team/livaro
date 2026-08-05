---
type: inbox
date: 2026-08-05
status: processed
related: ["[[2026 08 05 Thinking Session — Mağaza Paneli 3D İlerleme ve Stok Göstergesi]]"]
---

# PM Tartışması — 3D İlerleme Göstergesi ve Stok

> Kurucunun isteği üzerine iki PM ajanı çağrıldı, önce bağımsız değerlendirdiler, sonra birbirlerinin çıktısını okuyup tartıştılar. Bu not tartışmanın kaydıdır — **karar değildir**. Kararlar: [[2026 08 05 Thinking Session — Mağaza Paneli 3D İlerleme ve Stok Göstergesi]].

## Mercekler
- **PM A — Satıcı Deneyimi & Büyüme:** mağaza sahibi nerede kaybolur, nerede vazgeçer, nerede yanlış beklentiye girer.
- **PM B — Güven, Operasyon & Teknik Gerçeklik:** gösterdiğimiz bilgi gerçeği yansıtmazsa ne olur, hangi destek yükü kurucuya döner.

## Tur 1 — Bağımsız değerlendirmeler

### PM A'nın ana tezi
Asıl kopuş kurucunun tarif ettiği yerden **sonra**: üretim bitince kimseye haber gitmiyor. Mağaza paneli kapatırsa 3D'sinin hazır olduğunu ancak kendiliğinden geri dönerse öğrenir; ürün "mağaza onayı bekliyor"da çakılı kalır, admin onayına hiç gelmez, yayına çıkmaz. *"Yüzde ekranı ilk beş dakikayı güzelleştirir; ürünü yayına çıkaran şey bitiş bildirimidir."*

PM A'nın kendine özgü bulguları:
- **Yüzde işin tamamını anlatmıyor.** Tripo'dan gelen 0-100 sadece model üretimi adımı; sonrasında indirme, gerçek ölçüye büyütme, iPhone formatına çevirme var. Yüzde 100'e varır, ekran donar, ürün hâlâ "üretiliyor" görünür. Yüzdeyi 0-90'a sıkıştırmak veya sona "son hazırlıklar" adımı koymak gerekiyor.
- Sistemde "30 dakikadır üretimde olan ürün takılmış sayılır" kuralı var; kutucuk 30 dakika %60'ta dursa mağaza bu kuralın devreye girdiğini göremez.
- Başarısızlıkta **iki farklı son** var: hak kaldıysa ürün "Taslak"a döner (mağaza tekrar deneyebilir), hak bittiyse "Takıldı"ya düşer (mağazanın yapabileceği hiçbir şey yok). Tek genel mesaj ikinci gruptaki mağazayı boş yere bekletir.
- Kapatılan kutucuğun geri gelme yolu kurucunun isteğinde yok; olmazsa mağaza tek takip aracını kendi eliyle yok eder.

### PM B'nin ana tezi
İstek mantıklı ama **elimizde olmayan bir bilgiyi söz vermek** üzerine kurulu. Yüzde gerçek, süre değil. Ve yüzde ekranı bugün gizli kalan bir haksızlığı görünür yapacak.

PM B'nin kendine özgü bulguları:
- **Deneme hakkı gönderim anında düşüyor**, sistem hatasında geri verilmiyor; üstelik aynı fotoğraflarla tekrar deneme koda gömülü şekilde yasak. Hatası olmayan mağaza iki kez cezalandırılıyor. *"İnsanlar '%78'e geldi, sonra sistem yedi' diyecek ve destek talebi doğrudan sana gelecek."*
- **Kuyruk görünmüyor:** işler sırayla yapılıyor (eşzamanlılık ayarı yok). 10 ürün gönderilirse 10.'su 9 işin arkasında bekler; ona süre sözü vermek yanlış.
- Yeni deneme başlarken yüzde sıfırlanmazsa kullanıcı yeni denemenin başında eski denemenin "%87"sini görür.
- **Mağaza ürün listesi bugün 3D kaydının tüm alanlarını tarayıcıya gönderiyor** (iç iş numarası, sahiplik işareti, ham hata metni). Sahiplik kontrolü mağaza bazında doğru ama yeni bir ilerleme ucu açılırsa kontrol birebir tekrarlanmalı.
- **Hız sınırı yok**; 3D inceleme sayfası bugün 5 saniyede bir tüm ürün listesini çekiyor.
- **Katalogda kazanan stok değil, işaret:** yayın filtresi her yerde "yayında + stokta yok işareti basılı değil"; stok adedi hiçbir filtreye girmiyor. "Stok: 0" yazan ürün müşteriye satılmaya devam ediyor.
- Toplu Excel yükleme kodda henüz yok — kurucunun o senaryosu gelecekle ilgili.

## Tur 2 — Tartışma

### Anlaştıkları
- Süre ölçümü hiç yok, geriye dönük de çıkarılamaz (3D kaydı her denemede üzerine yazılıyor).
- 5 dakikalık kesme sınırı gerçek ve tek somut sayı — ama bu bir **başarısızlık eşiği**, tipik süre değil.
- Sistem hatasında hakkın yanması iki PM'in de **birinci öncelik** saydığı düzeltme.
- Yüzde 100 ≠ bitti; sona ayrı bir adım gerekiyor.
- Başarısızlıkta iki ayrı mesaj şart.
- Kapatılan kutucuğun geri gelme yolu şart.
- Mobilyada stok hiç sorulmuyor; halıda gösterilecek yüzde yok.
- Her denemenin başlama/bitme saati **hemen** kaydedilmeye başlanmalı.

### PM B'nin geri adım attığı iki nokta
1. **Kutucuğun yeri.** "Kurucu açıkça 'gezebilecek' dedi; sunucu yükü bunu engellemiyor. Engelleyen şey bugünkü yöntem." Yalnız üretimdekileri dönen küçük bir uç + 10-15 saniyelik aralık + sekme arka plandayken durdurma → kutucuk her sayfada yaşar, yük bugünkünden **az** olur.
2. **Süre yazısı.** "'Hiç yazmayalım' demek kurucunun açık isteğini reddetmekti." Dürüst ara yol var — ama şartı: verilen süre sözü **sıra beklemeyi kapsamamalı**, bekleyen üründe "sırada bekliyor" yazmalı.

### PM A'nın geri adım attığı nokta
Kendi "genelde 5 dakikadan kısa sürer" önerisini geri çekti: *"5 dakika sistemin başarısızlık eşiği, tipik süre değil. O cümle aslında '5 dakikayı geçerse zaten patlar' demek — söz gibi görünen bir uyarı."* Yerine önerdiği ara yol kabul edildi: önce "genelde birkaç dakika sürer", aynı anda süre ölçümü başlar, 20 gerçek üretim birikince ekran kendiliğinden "ortalama X dakika"ya döner.

### Kapanmayan iki ayrışma (kurucuya soruldu)
1. **Stok göstergesi.** PM A: "stokta yok" düğmesi kalksın, sayı tek doğru kaynak olsun. PM B buna sert itiraz etti: mobilyada stok hiç sorulmadığı için "stok 0 = otomatik kapat" kuralı **bütün mobilya kataloğunu düşürür**; ayrıca mağaza stoku varken ürünü geçici kapatmak isteyebilir (yanlış fiyat, fotoğraf yenileme, tedarik sorunu, tatil) ve sayı bunu ifade edemez. PM A ise PM B'nin "mobilyada kutucuk hiç görünmesin" cevabının kurucunun isteğini **ana kategoride tamamen boşa çıkardığını** söyledi. Uzlaşma önerisi: stoklu kategoride sayı, mobilyada "Satışta / Satışta değil" anahtarı. → Kurucu bu uzlaşmayı seçti.
2. **Onay düğmelerinin yeri.** PM A ayrı "3D'yi İncele" sayfasının kaldırılmasını istedi. PM B riskli buldu: *"Reddetmek geri alınamaz — bir deneme hakkı yanıyor ve mağaza aynı fotoğraflarla tekrar deneyemiyor. Bu düğmeleri, yanında 'Bilgileri Güncelle' düğmesi olan uzun bir formun altına koymak yanlış tıklama üretir."* → Kurucu PM A'nın önerisini seçti; PM B'nin itirazı kayıtlıdır ve tasarımda yanlış tıklama koruması gerektirir.

## Ortak öneri listesi (öncelik sırasıyla)
1. **Sistem hatasında deneme hakkını iade et, aynı fotoğraflarla yeniden denemeye izin ver.** → Kurucu kabul etti.
2. **Her denemenin başlama ve bitme saatini kaydet.** → Kurucu kabul etti (süre kararının parçası).
3. **3D modeli ve onayı düzenleme sayfasına taşı.** → Kurucu kabul etti.
4. **İlerleme için ayrı ve hafif bir veri ucu aç** (yalnız yüzde + durum döner, mağaza kontrolü birebir tekrarlanır). → Tasarım gereği kabul edildi, ayrı bir karar notu açılmadı.

Kurucuya sunulmayan tek öneri: PM A'nın "yüzde ekranının altına 'Bu sırada başka ürün ekleyin' düğmesi" fikri — kayıt için burada duruyor.

## Kaynak
- [[2026 08 05 Thinking Session — Mağaza Paneli 3D İlerleme ve Stok Göstergesi]]
