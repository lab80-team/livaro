---
type: decision
status: accepted
created: 2026-08-06
source: "[[2026 08 06 Thinking Session — Uygulama User Journey]]"
related: []
---

# Sepette ödeme butonu yok — dürüst bilgi satırı

## Bağlam
Kurucunun paylaştığı sepet görselinde siyah **"Siparişi Onayla"** butonu ve Ara Toplam / Kargo / Toplam satırları var. Ancak ödeme sağlayıcısı **seçilmedi**, emanet yapısı kurulmadı, sipariş modülü 24 Temmuz'da koddan söküldü. [[2026-07-24 Sepet MVP'de, checkout ödeme teknolojisi seçilince]] kararı sepeti "pasif liste" olarak tanımlıyordu.

## Karar
1. **"Siparişi Onayla" butonu MVP'de konmayacak.** Yerinde tek satır bilgi:
   > Şimdilik ödeme almıyoruz. Sepetiniz listeniz olarak kayıtlı kalıyor.
2. Sepet **pasif liste** olarak kalıyor — mağazaya talep/lead iletilmiyor.
3. Tasarım ekranındaki "Tümünü Sepete Ekle" tüm ürünleri tek sepette toplar; kullanıcı sepetten tek tek çıkarabilir.
4. Sepet boşken: "Sepetiniz boş" + "Beğendiğiniz ürünleri buraya ekleyin." + "Ürünlere göz at".

## Gerekçe
- Gri/pasif buton kullanıcıya "bozuk uygulama" hissi verir; çalışan bir buton ise yalan olur.
- "Mağazaya talep gönder" seçeneği için ne mağaza var (hiçbiriyle görüşülmedi) ne de gerçek e-posta altyapısı — ayrıca 24 Temmuz'da "talep iletilmez" kararı verilmişti.

## Değerlendirilen Alternatifler
- Buton gri/pasif dursun, "Yakında" yazsın.
- "Mağazaya talep gönder" olsun.

## Sonuçlar (Consequences)
- **Sepet bugün sıfırdan yapılacak bir özellik**: ekran boş yer tutucu ve veritabanında sepet tablosu bile yok.
- Ödeme sağlayıcısı seçilince bu karar yeniden konuşulacak.

## Riskler
- Kullanıcı "satın alamıyorum" diye ayrılabilir; dürüst satır bunu en azından beklenti hatasına çevirmiyor.

## İlgili Görevler
→ [[Task Board]]

## İlgili Bilgi
[[Marketplace Model]], [[30 Knowledge/Product/Product Flows|Product Flows (Knowledge)]]

## Kaynak Toplantı
[[2026 08 06 Thinking Session — Uygulama User Journey]]
