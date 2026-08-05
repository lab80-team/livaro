---
type: knowledge
status: living
updated: 2026-08-05
related: ["[[Seller Experience]]", "[[Marketplace Model]]"]
---

# Admin Panel

## Şu An Bilinenler

### Mevcut durum (inşa edilmiş, 2026-07-29 build, main'de)
- Ayrı bir site (`admin/`), yalnız kurucular girer. **Kasıtlı asgari** 3 ekran: **Başvurular** (mağaza kaydı onay/red), **Ürün Onayı** (AWAITING_ADMIN → PUBLISHED), **Takılanlar** (3D'si 2 kez başarısız STUCK ürünler; foto değiştirip Tripo'yu yeniden tetikleme) → [[2026-07-29 Build Oturumu — Mağaza Web ve Yönetim Sitesi]].
- ADMIN hesabı seed script'le açılıyor; panelden hesap yönetimi yok.
- Gerçek satıcı/kurucu kullanımı yok — **Validated değil**.

### v1 tasarımı (2026-08-04 thinking session'da kararlaştı)
Kaynak: [[2026 08 04 Thinking Session — Admin Paneli]] (2 PM'li tartışmayla: [[2026-08-04 PM Tartışması — Admin Paneli]]).

**İnşa durumu (2026-08-05):** v1 sekiz parçaya bölündü; **dilim 1 (parça 1-2-3) inşa edildi**, dal `feature/admin-panel-v1-slice1` — **main'e henüz birleştirilmedi** (sebep: [[2026-08-05 Build Oturumu — Admin Paneli Dilim 1]] §7). Kalan parçalar aşağıda tek tek işaretli.

- **Giriş/hesaplar**: yalnız yetkililer; başlangıçta 2 yetkili hesap; mevcut yetkili panelden yenisini ekleyebilir → [[2026-08-04 Admin hesap yönetimi — panelden yetkili ekleme]].
- **Ana sayfa = iş kuyruğu** (pilotta): 4 bekleyen sayacı (başvuru, ürün onayı, takılan 3D, düzenleme onayı) + son kaydolan mağaza/kullanıcı listeleri. Sütun/çizgi grafikler (günlük kullanıcı kaydı, satış vb.) **veri birikince** → [[2026-08-04 Admin panel v1 kapsamı — kuyruk ana sayfa, mağaza kartları, ciro-reklam alanları yok]].
- **Mağazalar sekmesi**: kartlar (logo, isim, açıklama, ürün sayısı, yayınlanmış 3D sayısı, kayıt tarihi) + sağ üstte kırmızı rozet (bekleyen ürün onayı + STUCK + düzenleme onayı toplamı); karta tıklayınca detay. Mağaza sayısı göstergesi = başvuran toplam (onaylı/bekleyen/reddedilen ayrımıyla).
- **Ürünler sekmesi**: tüm ürünler (durum, stok, 3D). Admin müdahalesi = **yayından kaldırma**; kalıcı silme yalnız yasaklı içerik, kayıtlı → [[2026-08-04 Admin ürün müdahalesi — yayından kaldırma, kalıcı silme yalnız yasaklı içerik]].
- **Yeniden onay** ✅ *(dilim 1'de inşa edildi)*: yayındaki üründe **yalnız vitrin alanları** (foto/başlık/açıklama) değişince ürün onay kuyruğuna düşer; stok/fiyat düşmez → [[2026-08-04 Ürün düzenlemede yeniden onay — yalnız vitrin alanları]]. İnşa sırasında üç davranış kararı eklendi:
  - **Ürün onay beklerken YAYINDA kalır**, müşteri onaylı eski hali görür; değişiklik ayrı bir "bekleyen düzenleme" kaydında durur. Vitrin alanını eski değerine geri yazmak o alanın önerisini **iptal eder** → [[2026-08-05 Yeniden onay davranışı — ürün yayında kalır, geri yazmak öneriyi iptal eder]].
  - **Yayındaki üründe fotoğraf değiştirme yolu açıldı** (bugüne kadar kasıtlı kapalıydı) — ayrı bir uçla, 3D'ye ve Tripo hak sayacına dokunmadan → [[2026-08-05 Yayındaki üründe fotoğraf değiştirme yolu açıldı]].
  - **"Onayla + 3D'yi yenile" ÇIKARILDI** — 4 Ağustos'ta kabul edilmişti, kod doğrulaması veri kaybı riskini gösterdi → [[2026-08-05 3D yenileme dilim 1'den çıkarıldı — veri kaybı riski]]. Foto-3D uyuşmazlığı bu yüzden hâlâ açık.
- **Kullanıcılar**: her kullanıcının kendi kartı — bütün bilgileri, uygulama kullanım istatistikleri ve RoomPlan çıktısı görünür (kurucu kararı, ikinci turda teyitli: "avukatla konuşup ayarlarız"; PM'lerin KVKK itirazı ve aydınlatma şartı kayıtlı) → [[2026-08-04 Kullanıcı kartı adminde — kişi bazlı kullanım verisi ve RoomPlan çıktısı]].
- **Ciro/satış/reklam alanları v1'de YOK** — ciro/satış ödeme kuruluşu + checkout sonrası, reklam sayıları "Sponsorlu" ürünü sonrası eklenecek (kurucunun uzun vadeli isteği kayıtlı: mağaza başına ciro, ürün başına reklam durumu).
- İstenen admin metrik vizyonu (2026-07-24'ten beri): ürün görüntüleme, tıklanma, kaç kişinin ürünle tasarım yaptığı, sepete eklenme → [[Seller Experience]].

- **İşlem günlüğü** ✅ *(dilim 1'de inşa edildi)*: onay/red işlemleri kim / ne zaman / red nedeni ile kaydedilir → [[2026-08-04 İşlem günlüğü ve sessiz olay defteri kabul edildi]]. Kayıt, tarif ettiği işlemle **aynı transaction içinde** yazılır (ateşle-unut olsaydı bir onay kaydı sessizce kaybolabilirdi). Ekranı yok — mağaza detay ekranıyla birlikte dilim 3'te gelecek.
- **Sessiz olay defteri** ✅ *(dilim 1'de inşa edildi, 3 tip)*: tek tablo, ekransız; pilottan önce açık olmalı; en dar kapsam → aynı karar notu. Kullanıcı kartındaki istatistiklerin veri kaynağı. İnşa gerçekleri:
  - **3 tip kaydediliyor**: ürün görüntüleme, tasarımda kullanım, tarama tamamlama. **Sepete ekleme YOK** — sepet henüz yok (iOS'taki Sepet sekmesi boş bir ekran); tablo tek ve tip bir kolon olduğu için sepet yapılınca değer eklemek tek migration.
  - **"Tasarımda kullanım" = "AI önerisinde çıktı"**, "kullanıcı bu ürünü seçti" DEĞİL. iOS sihirbazda her arama çalıştığında sonucu kaydediyor; kullanıcı üç kez arama yaparsa aynı ürün üç kez sayılır. Rakam okunurken bilinmeli.
  - **Ürün görüntüleme kişisiz**: iOS ürün detayını kimlik göndermeden çekiyor → "kaç kez bakıldı" kaydedilir, "kim baktı" kaydedilmez. Kişi bazlı istenirse iOS değişikliği + yeni sürüm gerekir → [[Open Questions]].
  - **Canlı yola henüz eklenmedi**: gerçek kullanıcılar Supabase edge function'a gidiyor, oradaki kanca Görev 10'da eklenecek — **saatte bir kez sayma** şartıyla → [[2026-08-05 Ürün görüntüleme olayı saatte bir kez sayılır]].

## Varsayımlar
- İki kişilik ekibin onay kuyruklarını (başvuru + ürün + düzenleme + STUCK) eritebileceği — pilotta gözlenecek.

## Bilinmeyenler
- v1'in kalan dilimlerinin (2-3-4) zamanlaması, pilot-öncesi öncelikler karşısındaki sırası — **To Be Decided**. (Dilim 1'in sırası 2026-08-05'te karara bağlandı: veri temeli önce.)
- Grafiklerin ekleneceği "veri birikti" eşiği — **Unknown**.
- ~~Foto değişikliği onaya düşünce 3D'nin yeniden tetiklenip tetiklenmeyeceği~~ — **ÇÖZÜLDÜ (2026-08-05)**: 3D yenileme dilim 1'den çıkarıldı, foto onaylandığında 3D **aynı kalıyor** → [[2026-08-05 3D yenileme dilim 1'den çıkarıldı — veri kaybı riski]]. **Yeni açık soru**: foto-3D uyuşmazlığı ne zaman/nasıl kapatılacak (güvenli 3D yenileme ayrı bir dilim olarak sıraya girdi, beş şartı karar notunda yazılı).
- KVKK aydınlatma metninin kullanıcı kartı gösterimini kapsayacak şekilde ne zaman hazırlanacağı — **To Be Decided** → [[Open Questions]].
- Kişi bazlı ürün görüntüleme istenirse gereken iOS değişikliği ne zaman yapılacak — **To Be Decided** → [[Open Questions]].

## İlgili Notlar
- [[Seller Experience]], [[Marketplace Model]], [[System Architecture]]

## Kaynaklar
- [[2026-08-05 Build Oturumu — Admin Paneli Dilim 1]] (dilim 1 inşası)
- [[2026 08 04 Thinking Session — Admin Paneli]]
- [[2026-08-04 PM Tartışması — Admin Paneli]]
- [[2026-07-29 Build Oturumu — Mağaza Web ve Yönetim Sitesi]]
