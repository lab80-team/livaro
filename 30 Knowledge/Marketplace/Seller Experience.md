---
type: knowledge
status: living
updated: 2026-07-20
related: []
---

# Seller Experience

## Şu An Bilinenler
- **Satıcı web paneli (brand-panel) prototipte mevcut** (Haziran, Faz 3): Vite + React Router; yalnızca SELLER/ADMIN rolleri girebilir (CUSTOMER engellenir). Kaynak: [[2026-07-08 Oturum Import — Web Temelleri ve iOS Başlangıcı]].
- **Ürün yükleme akışı çalışıyor**: form (ad, açıklama, fiyat, **en/boy/yükseklik cm — üçü zorunlu** çünkü 3D model gerçek ölçülere göre scale ediliyor; kumaş opsiyonel) + **4 açı fotoğrafı (ön/arka/sol/sağ)** — Tripo3D multi-view 3D model üretiminin girdisi. Kaydetme resumable state machine: ürün oluştur → fotoğrafları yükle → 3D pipeline tetikle; hatada "Tekrar dene" kaldığı adımdan sürer.
- slug/sku gibi teknik alanlar satıcıdan gizlenip otomatik üretiliyor. Markası olmayan satıcı ürün ekleyemez (bilinçli engelleme mesajı).
- Görsel kimlik: "Sıcak/Lüks" — koyu kahve-siyah #1C1917 + altın #A16207, dark-first, Inter (kurucu seçimi, 17-19 Haz).
- Maliyet notu: 3D pipeline retry'ı Tripo3D sonucunu cache'lemiyor — her "Yeniden dene" gerçek kredi harcar (bkz. [[Known Pitfalls]]).
- brand-panel'in **güncel bakım durumu belirsiz**: Temmuz oturumları tamamen iOS/3D'ye odaklandı; panelin bu dönemde test edilip edilmediği **Needs Validation**.

## Varsayımlar
- Satıcıların 4 açı fotoğrafı çekme zahmetine katlanacağı — **Needs Validation** (hiç gerçek satıcıyla test edilmedi).

## Bilinmeyenler
- Satıcıların kim olacağı (mağazalar, bireysel, üreticiler) — **Unknown**. Kurucu beyanı (2026-07-21): **satıcı adayı var, henüz görüşülmedi** (kaynak: [[2026-07-21 PM Panel Tartışması]]).
- Satıcı onboarding'i (davet mi, self-serve mi) — **To Be Decided**.
- Katalog import/entegrasyon ihtiyacı — **Unknown**.

## Önemli Sorular
- Satıcı tarafı MVP'de mi? Katalog kim tarafından doldurulacak (ilk fazda ekip mi, satıcılar mı)?
- Tripo3D çıktı kalitesi gerçek mobilya çeşitliliğinde yeterli mi?

## İlgili Notlar
- [[Marketplace Model]], [[60 Planning/Product Flows|Product Flows]], [[2026-06-22 iOS uygulaması yalnızca müşteri tarafı]]

## Kaynaklar
- [[2026-07-08 Oturum Import — Web Temelleri ve iOS Başlangıcı]]
