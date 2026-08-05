---
type: decision
status: accepted
created: 2026-08-05
source: "[[2026-08-05 Build Oturumu — Admin Paneli Dilim 1]]"
related: ["[[Admin Panel]]", "[[2026-08-04 Ürün düzenlemede yeniden onay — yalnız vitrin alanları]]"]
---

# "Onayla + 3D'yi yenile" dilim 1'den çıkarıldı — veri kaybı riski

## Bağlam

4 Ağustos'ta kurucuya soruldu: yayındaki ürünün fotoğrafı değişip onaylandığında 3D modele ne olsun? Kurucu **"onay ekranında admin seçsin"** dedi — iki buton: "Onayla" ve "Onayla + 3D'yi yenile".

İnşadan önce koşulan kod tabanı doğrulaması, bu seçeneğin bugünkü boru hattında **veri kaybına yol açtığını** gösterdi.

## Karar

**"Onayla + 3D'yi yenile" seçeneği dilim 1'den çıkarıldı.** Onay ekranında yalnız "Onayla" (yeni foto/başlık yayına geçer, 3D aynı kalır) ve "Reddet" var. 3D yenileme, güvenli hâliyle ayrı bir iş olarak sıraya girdi.

## Gerekçe

Dört ayrı kod gerçeği üst üste bindiğinde sonuç geri dönüşsüz:

1. **Kapı yok.** Yayındaki bir ürünü 3D üretimine sokan hiçbir kod yolu yok; mevcut iki kapı da (`canAdminRetry`, `canSubmitTo3D`) PUBLISHED ürünü reddediyor.
2. **Yayındaki model üretim başlar başlamaz siliniyor.** Ürünün tek bir 3D model satırı var; yeni üretim başlarken model adresleri boşaltılıyor.
3. **Dosyalar üzerine yazılıyor.** İşçi yeni modeli aynı depo adresine yazıyor; eski, parası ödenmiş dosya kurtulmuyor (depoda sürümleme yok).
4. **Geri dönüş yolu yok.** Üretim başarısız olursa ürün taslağa ya da "takıldı"ya düşüyor; yayına döndüren hiçbir yol yok — ürün katalogdan tamamen çıkıyor.

Net sonuç: **bir kez patlayan yenileme, çalışan bir ürünü kalıcı olarak yayından düşürür, parası ödenmiş 3D varlığını yok eder ve o ürünle yapılmış kayıtlı tasarımları bozar.**

## Değerlendirilen Alternatifler

- **Güvenli hâlini dilim 1'e katmak** — yeni model ayrı adrese üretilir, eski model hazır olana kadar yayında kalır, üretim patlarsa hiçbir şey kaybolmaz. Doğru çözüm ama dilim 1'i kabaca iki katına çıkarır ve 3D boru hattının en riskli yerini değiştirir. **Ertelendi.**
- **Basit hâliyle yapıp riski kabul etmek** — kurucuya sunuldu, seçilmedi.

## Sonuçlar (Consequences)

- Fotoğraf onaylandığında 3D model **eski fotoğraflardan üretilmiş hâliyle kalır**; foto ile 3D arasında uyuşmazlık oluşabilir. Bilinçli kabul.
- `lastImageSetHash` alanı onay anında **yazılmıyor** — o alan 3D üretiminde *kullanılan* seti işaretliyor; yazmak, üretilmemiş bir modeli üretilmiş gibi göstermek olurdu. Kodda testle sabitlendi.
- Onayda eski fotoğraflar depodan **silinmiyor** — 3D model kaydı o dosyalara bakıyor.

## Riskler

- Foto-3D uyuşmazlığı pilotta müşteriye yanlış model gösterebilir. Ölçülmedi; 3D yenileme işi sıraya girene kadar açık.

## Güvenli hâli için gereken beş şart (ayrı dilim)

1. Durum makinesine yeni bir saf kapı fonksiyonu (hak sayacına bakmayan, yalnız PUBLISHED kabul eden).
2. Yeni üretimin **ayrı bir depo adresine** yazması; eski dosyanın üzerine yazılmaması.
3. Üretim sırasında model adreslerinin boşaltılmaması — eski model yenisi hazır olana kadar yayında kalmalı.
4. Başarısızlıkta ürünün PUBLISHED kalması (ürün hiç yayından inmemeli).
5. Durum makinesinin kapsam testlerinin bilinçli olarak güncellenmesi.

## İlgili Görevler

3D yenileme ayrı bir dilim olarak sıraya girdi → [[Task Board]].

## İlgili Bilgi

[[Admin Panel]], [[Seller Experience]]

## Kaynak

[[2026-08-05 Build Oturumu — Admin Paneli Dilim 1]]
