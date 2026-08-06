---
type: decision
status: accepted
created: 2026-08-06
source: "[[2026 08 06 Thinking Session — Uygulama User Journey]]"
related: []
---

# Tasarım beklemesi arka planda sürer — üst şerit haber verir

## Bağlam
4 soru cevaplandıktan sonra yapay zekâ tasarımı üretiyor ve fotogerçekçi görüntü hazırlanıyor. Bu bekleme bugün **tam ekran** ve kullanıcı çıkarsa iş kayboluyor. Süre **hiç ölçülmedi** — ekranda duran "~2-3 dakika" yazısı hiçbir ölçüme dayanmıyor.

Ayrıca teknik bir engel var: uygulama sunucuya soru sorarken 60 saniyelik varsayılan sınırı kullanıyor; 60 saniyeyi aşan her işlem **"Bağlantı hatası. İnternet bağlantınızı kontrol edin."** diye düşüyor — internet gayet iyiyken.

## Karar
[[2026-08-05 3D ilerleme göstergesi — her sayfada kapatılabilir kutucuk]] kararının müşteri tarafındaki karşılığı kuruluyor:

1. **Bekleme ekranı yüzde göstermez, adım listesi gösterir** (Blender işinin yüzdesi yok): "Odanız hazırlandı ✓ / Tasarım kuruluyor ◐ / Fotogerçekçi görüntü alınıyor ○".
2. **"Arka planda devam et"** butonu: basınca kullanıcı 5 sekmede özgürce gezer.
3. Sekmelerin üstünde ince şerit: **"Salon tasarlanıyor…"** + "Görüntüle". Bitince şerit **kaybolmaz**, yeşile döner: **"Salon tasarımınız hazır"**.
4. Uygulamadan tamamen çıkılıp dönülürse: Projelerim'de o oda **"Tasarlanıyor"** etiketiyle görünür.
5. **Süre yazısı**: önce "Genelde birkaç dakika sürer." Ölçüm başlar; **20 gerçek tasarım sonra** "Genelde ortalama X dakika sürer"e geçilir. (Mağaza tarafındaki [[2026-08-05 3D süre yazısı — önce tahmin, 20 üretim sonra gerçek ortalama]] kararının aynısı.)
6. **Bildirim MVP'de yok ve söz verilmez** — iOS tarafında bildirimle ilgili tek satır kod yok.
7. **İş sunucuda başlatılır, telefon sadece durumu sorar** — 60 saniye sınırını aşmanın tek yolu bu.

## Gerekçe
- Aynı problem için iki ayrı yerde iki ayrı kural yazmak 2 kişilik ekipte gereksiz bakım yükü.
- Uydurma yüzde çubuğu konmuyor: mağaza panelinde "%100'de donan ekran" sorunu tam bu yüzden hâlâ açık.
- Bekleme sırasında çıkan kullanıcının emeği bugün kayboluyor ve her yeni deneme gerçek para yakıyor.

## Değerlendirilen Alternatifler
- **Tam ekran bekleme, çıkış yok** (bugünkü davranış): 60 saniye sınırıyla birleşince yanlış hata mesajı üretiyor.
- **Hiç bekleme ekranı olmaması**: kullanıcı ne olduğunu anlamıyor.

## Sonuçlar (Consequences)
- Tasarım isteği "başlat + durum sor" yapısına dönecek (görev: [[Task Board]]).
- Her tasarımın başlama/bitiş saati kaydedilecek — ölçüm sonradan telafi edilemiyor (mağaza tarafında bu ders zaten yaşandı).
- `RenderGalleryView`'daki ölçülmemiş "~2-3 dakika" yazısı kaldırılacak.
- Tasarım ancak sunucu cevabı geldiğinde kaydediliyor ve kaydetme hatası yutuluyor — bu düzeltilecek.

## Riskler
- Süre gerçekten uzunsa (ölçülmedi) şerit yaklaşımı bile yetmeyebilir; ölçüm sonrası kalite/süre dengesi yeniden konuşulmalı.

## İlgili Görevler
→ [[Task Board]]

## İlgili Bilgi
[[3D Render Pipeline]], [[Known Pitfalls]]

## Kaynak Toplantı
[[2026 08 06 Thinking Session — Uygulama User Journey]]
