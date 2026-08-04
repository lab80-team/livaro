---
type: decision
status: accepted
created: 2026-08-04
source: "[[2026 08 04 Thinking Session — Admin Paneli]]"
related: ["[[Admin Panel]]"]
---

# Admin hesap yönetimi — 2 yetkili, panelden yetkili ekleme

## Bağlam
Admin hesabı bugün kurulum betiğiyle (seed script) açılıyor; panelden hesap yönetimi yok. Kurucu "iki yetkili giriş hesabı" ve admin'e yalnız yetkililerin girmesini istedi.

## Karar
- Admin paneline yalnız yetkililer girer; başlangıçta **2 yetkili hesap** (iki ayrı kişisel hesap).
- **Mevcut yetkili panelden yeni yetkili ekleyebilir** (seed script'e bağımlılık kalkar).
- Yeni mağaza kayıtları yalnız yetkili onayıyla açılır (mevcut Başvurular akışı — değişiklik yok).

## Gerekçe
Kurucu tercihi: esneklik (üçüncü kişi gerektiğinde geliştirici müdahalesi olmadan eklenebilsin). PM-A'nın önerisi sabit 2 hesaptı (en güvenlisi); kurucu panelden eklemeyi seçti.

## Değerlendirilen Alternatifler
- Sabit 2 hesap, panelden ekleme yok (PM-A önerisi) — reddedildi.

## Sonuçlar (Consequences)
- Panelde "yetkili ekle" ekranı gerekir.
- Yetkili ekleme/çıkarma işlemlerinin izlenebilir olması önem kazanıyor (işlem günlüğü önerisiyle bağlantılı → [[Open Questions]]).

## Riskler
- Panelden hesap açma, yanlışlıkla/kötüye kullanım yüzeyi ekler (PM-A'nın itiraz gerekçesi — kayıtlı).

## İlgili Görevler
Yok.

## İlgili Bilgi
[[Admin Panel]], [[System Architecture]]

## Kaynak Toplantı
[[2026 08 04 Thinking Session — Admin Paneli]]
