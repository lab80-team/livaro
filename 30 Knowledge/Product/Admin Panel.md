---
type: knowledge
status: living
updated: 2026-08-04
related: ["[[Seller Experience]]", "[[Marketplace Model]]"]
---

# Admin Panel

## Şu An Bilinenler

### Mevcut durum (inşa edilmiş, 2026-07-29 build, main'de)
- Ayrı bir site (`admin/`), yalnız kurucular girer. **Kasıtlı asgari** 3 ekran: **Başvurular** (mağaza kaydı onay/red), **Ürün Onayı** (AWAITING_ADMIN → PUBLISHED), **Takılanlar** (3D'si 2 kez başarısız STUCK ürünler; foto değiştirip Tripo'yu yeniden tetikleme) → [[2026-07-29 Build Oturumu — Mağaza Web ve Yönetim Sitesi]].
- ADMIN hesabı seed script'le açılıyor; panelden hesap yönetimi yok.
- Gerçek satıcı/kurucu kullanımı yok — **Validated değil**.

### v1 tasarımı (2026-08-04 thinking session'da kararlaştı, henüz İNŞA EDİLMEDİ)
Kaynak: [[2026 08 04 Thinking Session — Admin Paneli]] (2 PM'li tartışmayla: [[2026-08-04 PM Tartışması — Admin Paneli]]).

- **Giriş/hesaplar**: yalnız yetkililer; başlangıçta 2 yetkili hesap; mevcut yetkili panelden yenisini ekleyebilir → [[2026-08-04 Admin hesap yönetimi — panelden yetkili ekleme]].
- **Ana sayfa = iş kuyruğu** (pilotta): 4 bekleyen sayacı (başvuru, ürün onayı, takılan 3D, düzenleme onayı) + son kaydolan mağaza/kullanıcı listeleri. Sütun/çizgi grafikler (günlük kullanıcı kaydı, satış vb.) **veri birikince** → [[2026-08-04 Admin panel v1 kapsamı — kuyruk ana sayfa, mağaza kartları, ciro-reklam alanları yok]].
- **Mağazalar sekmesi**: kartlar (logo, isim, açıklama, ürün sayısı, yayınlanmış 3D sayısı, kayıt tarihi) + sağ üstte kırmızı rozet (bekleyen ürün onayı + STUCK + düzenleme onayı toplamı); karta tıklayınca detay. Mağaza sayısı göstergesi = başvuran toplam (onaylı/bekleyen/reddedilen ayrımıyla).
- **Ürünler sekmesi**: tüm ürünler (durum, stok, 3D). Admin müdahalesi = **yayından kaldırma**; kalıcı silme yalnız yasaklı içerik, kayıtlı → [[2026-08-04 Admin ürün müdahalesi — yayından kaldırma, kalıcı silme yalnız yasaklı içerik]].
- **Yeniden onay**: yayındaki üründe **yalnız vitrin alanları** (foto/başlık/açıklama) değişince ürün onay kuyruğuna düşer; stok/fiyat düşmez → [[2026-08-04 Ürün düzenlemede yeniden onay — yalnız vitrin alanları]].
- **Kullanıcılar**: her kullanıcının kendi kartı — bütün bilgileri, uygulama kullanım istatistikleri ve RoomPlan çıktısı görünür (kurucu kararı; PM'lerin KVKK itirazı ve aydınlatma şartı kayıtlı) → [[2026-08-04 Kullanıcı kartı adminde — kişi bazlı kullanım verisi ve RoomPlan çıktısı]].
- **Ciro/satış/reklam alanları v1'de YOK** — ciro/satış ödeme kuruluşu + checkout sonrası, reklam sayıları "Sponsorlu" ürünü sonrası eklenecek (kurucunun uzun vadeli isteği kayıtlı: mağaza başına ciro, ürün başına reklam durumu).
- İstenen admin metrik vizyonu (2026-07-24'ten beri): ürün görüntüleme, tıklanma, kaç kişinin ürünle tasarım yaptığı, sepete eklenme → [[Seller Experience]].

### PM önerileri (öneri statüsünde — kurucuya ayrıca onaylatılmadı)
- **İşlem günlüğü**: kim neyi onayladı/reddetti + red nedeni kaydı (iki PM ortak önerisi).
- **Sessiz olay defteri**: 4 olay tipi (ürün görüntüleme, tasarımda kullanım, sepete ekleme, tarama tamamlama), tek tablo, ekransız; "geçmiş veri sonradan satın alınamaz" gerekçesiyle pilottan önce açılması önerildi. Kullanıcı kartındaki "kullanım istatistikleri" bunu fiilen gerektiriyor.
→ İkisi de [[Open Questions]]'da.

## Varsayımlar
- İki kişilik ekibin onay kuyruklarını (başvuru + ürün + düzenleme + STUCK) eritebileceği — pilotta gözlenecek.

## Bilinmeyenler
- v1'in inşa zamanlaması (pilot-öncesi öncelikler karşısındaki sırası) — **To Be Decided**.
- Grafiklerin ekleneceği "veri birikti" eşiği — **Unknown**.
- Foto değişikliği onaya düşünce 3D'nin yeniden tetiklenip tetiklenmeyeceği — **To Be Decided** → [[Open Questions]].
- KVKK aydınlatma metninin kullanıcı kartı gösterimini kapsayacak şekilde ne zaman hazırlanacağı — **To Be Decided** → [[Open Questions]].

## İlgili Notlar
- [[Seller Experience]], [[Marketplace Model]], [[System Architecture]]

## Kaynaklar
- [[2026 08 04 Thinking Session — Admin Paneli]]
- [[2026-08-04 PM Tartışması — Admin Paneli]]
- [[2026-07-29 Build Oturumu — Mağaza Web ve Yönetim Sitesi]]
