---
type: decision
status: accepted
created: 2026-07-29
source: "[[2026-07-29 Build Oturumu — Mağaza Web ve Yönetim Sitesi]]"
related: ["[[2026-07-29 3D üretimi 4 açının tamamını kullanır — Tripo multiview_to_model]]", "[[Seller Experience]]"]
---

# Yeni fotoğraf seti eskisinin yerine geçer, tekil silme yok

## Bağlam
Aynı build oturumunda (2026-07-29), uçtan uca kabul turu ikinci bir hata buldu: `POST /products/:id/images` fotoğrafı ürünün `images` dizisine yalnızca EKLİYORDU (Prisma `push`); hiçbir uç tek bir fotoğrafı silmiyordu, panelde de "sil" butonu yoktu. Sonuç: bir ürün reddedilip "farklı fotoğraflarla tekrar deneyin" denildiğinde, satıcı yeni 4 fotoğraf yüklediğinde dizi 8, 12... fotoğrafa büyüyordu (eskiler + yeniler); üretime de (gerçek modda) dizinin TAMAMI gidiyordu — eski reddedilmiş fotoğraflar yeniyle karışıyordu. Bu, [[2026-07-29 3D üretimi 4 açının tamamını kullanır — Tripo multiview_to_model|4-açı kararıyla]] birleşince "reddet ve farklı fotoğrafla dene" akışını fiilen işlemez hale getiriyordu.

Kurucuya soruldu; kurucu karar verdi.

## Karar
Yeni bir foto seti yüklendiğinde **eski set tamamen silinir, yenisiyle değiştirilir** (accumulate değil, replace).

## Gerekçe
Satıcının "farklı fotoğraflarla tekrar dene" ihtiyacı basit bir değiştirme davranışıdır; tekil silme arayüzü ekstra UI karmaşıklığı ekler ve asıl sorunu (eski+yeni karışımı) çözmek için yine de "hepsini sil, hepsini yükle" adımına ihtiyaç duyar.

## Değerlendirilen Alternatifler
- Satıcıya per-foto silme arayüzü eklemek — reddedildi (gereksiz karmaşıklık; ana kullanım senaryosu "yeni bir setle baştan çek").

## Sonuçlar (Consequences)
- Atomik `PUT /seller/products/:id/photos` ucu yazıldı: 4 fotoğraf da başarıyla yüklenmeden DB güncellenmiyor (yükleme yarıda kesilirse eski set kalıcı kaybolmasın diye).
- `replacePhotos`'ta check-then-act yarışı bulundu (4 yükleme penceresi boyunca ürün durumu garanti değildi) → reponun kendi CAS deseniyle (updateMany + status koşulu + ConflictException) korundu.
- `imageSetHash` sıraya duyarlı hale getirildi — aynı-fotoğraf-engeli kararıyla ([[2026-07-28 Ürün yükleme ve panel — 3D zorunlu, Tripo 2 hak]]) birlikte doğru çalışması için.

## Kaynak Toplantı
Bu bir toplantı kararı değil — mağaza web + yönetim sitesi build oturumunda (2026-07-29), uçtan uca kabul turunun bulduğu bir hata üzerine kurucuya doğrudan soruldu, kurucu karar verdi. Kayıt: [[2026-07-29 Build Oturumu — Mağaza Web ve Yönetim Sitesi]] (kod reposu ayrıntısı: `.superpowers/sdd/progress.md`, Task 24-25).
