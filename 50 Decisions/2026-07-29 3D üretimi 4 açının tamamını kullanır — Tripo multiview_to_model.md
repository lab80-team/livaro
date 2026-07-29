---
type: decision
status: accepted
created: 2026-07-29
source: "[[2026-07-29 Build Oturumu — Mağaza Web ve Yönetim Sitesi]]"
related: ["[[Seller Experience]]", "[[2026-07-28 Ürün yükleme ve panel — 3D zorunlu, Tripo 2 hak]]", "[[2026-07-29 Yeni fotoğraf seti eskisinin yerine geçer, tekil silme yok]]"]
---

# 3D üretimi 4 açının tamamını kullanır (Tripo multiview_to_model)

## Bağlam
Mağaza web + yönetim sitesi build oturumunda (2026-07-29), uçtan uca kabul turu bir hata ortaya çıkardı: satıcı formu 4 açı fotoğraf istiyordu (ön/arka/sol/sağ) ama kod Tripo'ya yalnız İLK fotoğrafı gönderiyordu (`type: 'image_to_model'`, `file_token: imageTokens[0]`) — yani vault'un o zamana kadar [[Seller Experience]]'da yazdığı "4 açı fotoğrafı Tripo3D multi-view 3D model üretiminin girdisi" bilgisi **yanlıştı**; gerçekte tek fotoğraflık kalitede model üretiliyordu. Bu, ikinci bir hatayla (fotoğrafların eskiye eklenmesi, değiştirilmemesi — bkz. [[2026-07-29 Yeni fotoğraf seti eskisinin yerine geçer, tekil silme yok]]) birleşince, satıcı kötü bir modeli asla yeniden çekim yaparak düzeltemiyordu: "farklı fotoğraflarla tekrar dene" her zaman orijinal ilk fotoğraftan yeniden üretiyor, iki Tripo hakkını da boşa harcayıp ürünü admin'in "takıldı" kuyruğuna itiyordu.

Kurucuya soruldu; kurucu karar verdi.

## Karar
3D üretimi Tripo'nun **`multiview_to_model`** ucunu kullanacak, 4 açının (ön/arka/sol/sağ) TAMAMINI `files=[front,left,back,right]` olarak gönderecek — tek-fotoğraf üretimi (`image_to_model`) terk edildi.

## Gerekçe
Satıcıdan zaten 4 açı fotoğrafı isteniyordu (form + çekim rehberi); ama üretim yalnızca birini kullanıyordu — vaat edilen kalite ile gerçek kalite arasında boşluk vardı. 4 açının tamamını kullanmak modelin gerçek şekli yakalama şansını artırır ve satıcının 4 fotoğraf çekme emeğini gerçekten değerlendirir.

## Değerlendirilen Alternatifler
- Tek-fotoğraf üretimini koru, yalnız EN YENİ fotoğrafı kullan (daha basit düzeltme, 4 açı toplama emeğini boşa çıkarır) — reddedildi.

## Sonuçlar (Consequences)
- Tripo sözleşmesi bağımsız doğrulandı (resmi doküman + Python SDK): `multiview_to_model`, `files=[front,left,back,right]`, eksik görünüm `{}` ile, `front` zorunlu, minimum 2 görünüm.
- Mevcut çekim rehberi sırası [ön,arka,sol,sağ] Tripo'nun beklediği sıradan farklı çıktı (arka↔sol takası) — ayrıca Tripo'nun "sol"u NESNENİN kendi solu (gerçek ayna-model riski). Bu, bağımlı bir dizi düzeltmeyi tetikledi: web/ ve admin/'de 4 ETİKETLİ foto slotu (serbest çoklu-seçim kaldırıldı), atomik foto yükleme ucu, rehber metninin "ürünün kendi solu" diye netleştirilmesi (mekanik tarif: "ön noktadan sağa yürü = Sol"), tam-4-foto şartı, sıraya duyarlı `imageSetHash`. Detay: [[2026-07-29 Build Oturumu — Mağaza Web ve Yönetim Sitesi]].
- [[Seller Experience]]'daki yanlış bilgi düzeltildi ve neden yanlış olduğu kayda geçirildi.

## Riskler
- **Gerçek bir tek-ürün multi-view Tripo denemesi henüz koşulmadı** (her şey `TRIPO3D_FAKE=1` ile test edildi, kredi harcanmadı) — ön/arka/sol/sağ → Tripo front/left/back/right eşlemesinin gerçekten doğru (aynalanmamış) model ürettiği, kurucu onaylı gerçek bir denemeyle teyit edilmeli → [[Open Questions]].

## Kaynak Toplantı
Bu bir toplantı kararı değil — mağaza web + yönetim sitesi build oturumunda (2026-07-29), uçtan uca kabul turunun bulduğu bir hata üzerine kurucuya doğrudan soruldu, kurucu karar verdi. Kayıt: [[2026-07-29 Build Oturumu — Mağaza Web ve Yönetim Sitesi]] (kod reposu ayrıntısı: `.superpowers/sdd/progress.md`, Task 24-25).
