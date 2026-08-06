---
type: decision
status: accepted
created: 2026-08-06
source: "[[2026 08 06 Thinking Session — Uygulama User Journey]]"
related: []
---

# Keşfet ve Profil ekran kapsamı

## Bağlam
Keşfet'in **markalar mı ürünler mi** göstereceği 24 Temmuz'dan beri karara bağlanmamıştı. Profil ekranı hiç tanımlanmamıştı. Kurucu ikisi için de referans görsel paylaştı.

## Karar

### Keşfet
1. Üstte **kategori satırı** (koltuk, halı, perde…), altında **2 sütunlu ürün ızgarası** (görsel + ad + fiyat + sağ üstte kalp) — paylaşılan görseldeki gibi.
2. **Filtre çubuğu MVP'de sadece "Sırala"** içerecek. "Filtrele", "Fiyat" ve "Marka" katalog dolunca eklenecek — bugün katalogda 3 test ürünü var.
3. Arama alanı MVP'de yok.

### Profil
1. **Görseldeki tam liste kalıyor**: üst kart (avatar + isim + e-posta/telefon), üç sayaç (Projelerim / Favoriler / Siparişlerim), liste satırları (Siparişlerim, Adreslerim, Ödeme Yöntemleri, Bildirimler, Ayarlar, Yardım & Destek), kırmızı "Çıkış Yap".
2. Sistemi olmayan satırlara (**Siparişlerim, Adreslerim, Ödeme Yöntemleri**) dokununca **"Yakında"** ekranı açılır.
3. Misafir kullanıcıda en üstte "Giriş Yap" kartı, sayaçlar yok.
4. **Gizlilik/KVKK metinleri** listeye eklenecek (yasal gereklilik).

## Gerekçe
- Keşfet: pilotta 4-6 marka olacağı için marka önde bir sayfa çok boş görünürdü; ürün ızgarası bugünkü katalogla da anlamlı.
- Profil: kurucunun tercihi — gelecekteki ürünü kullanıcıya baştan göstermek.

## Değerlendirilen Alternatifler
- Keşfet'te markalar önde, içinde ürünler.
- Keşfet'te tüm filtre çubuğunun MVP'de olması.
- Profilde Siparişlerim/Adreslerim/Ödeme Yöntemleri'nin **hiç gösterilmemesi** — iki yöneticinin tavsiyesi buydu (arkasında sistem yok, kullanıcıda "sipariş verebiliyorum" beklentisi yaratır; sipariş modülü 24 Temmuz'da koddan söküldü). Kurucu tam listeyi seçti; itiraz kayıtta.
- Profilde satırların gri "Yakında" etiketiyle tıklanamaz durması.

## Sonuçlar (Consequences)
- "Siparişlerim" sayacı bugün gösterilecek gerçek bir veriye sahip değil — 0 gösterecek.
- "Yakında" ekranı tek bir ortak bileşen olarak yazılacak.
- Keşfet'te sıralama ölçütü (fiyat/yenilik) tanımlanacak.

## Riskler
- Ölü menü satırları ilk kullanıcıda hayal kırıklığı yaratabilir (yöneticilerin itirazı).

## İlgili Görevler
→ [[Task Board]]

## İlgili Bilgi
[[30 Knowledge/Product/Product Flows|Product Flows (Knowledge)]], [[Marketplace Model]]

## Kaynak Toplantı
[[2026 08 06 Thinking Session — Uygulama User Journey]]
