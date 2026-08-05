---
type: import
source: claude-session
date: 2026-08-05
---

# 2026-08-05 Halı Kalınlık Doğrulaması Düzeltmesi (kod reposu)

Kaynak: 5 Ağustos Claude oturumu (kod reposunda düzeltme; vault'a işleme aynı gün).

## Sorun (canlıda doğrulandı)
- Panel, halı (flat) kategorisinde kalınlık alanına 0,1 cm'e kadar izin veriyordu; backend DTO'daki koşulsuz `@Min(1)` ise `heightCm: 0.8` gönderen `POST /api/seller/products`'a "heightCm must not be less than 1" 400'ü döndürüyordu.
- Sonuç: gerçek bir halı (0,8 cm hav) panelden **hiç kaydedilemiyordu**. Paneldeki yorum ("Backend en az 1 mm istiyor") niyeti doğru yazmış, backend uygulamamıştı — iki katman ayrışmıştı.

## Yapılan
- DTO tabanı 0,1 cm'e indirildi (`FLAT_MIN_HEIGHT_CM = MIN_THICKNESS_MM`, tek kaynak); en/boy 1 cm kaldı.
- Kategoriye duyarlı sıkı sınır serviste: flat ≥ 0,1 cm; mobilya/perde/bilinmeyen ≥ 1 cm. Update, kayıt sonrası geçerli olacak kategori+kalınlık çiftini doğrular (hali→mobilya dönüşümünde kayıtlı 0,8 de yakalanır).
- TDD ile: önce başarısız testler, sonra düzeltme.

## Codex inceleme turları (3 tur, merge kapısı gereği)
1. **1. tur, 3 bulgu (hepsi doğrulanıp düzeltildi):** açık `heightCm: null` "gönderilmedi" sanılıyordu (PartialType/IsOptional null'u geçiriyor, `{ ...dto }` NULL yazıyor — ölçülerek doğrulandı); CAS yalnız status'e bakınca iki eşzamanlı güncelleme kuralsız çift (mobilya + 0,8) bırakabiliyordu; 0,1 sabiti DTO'da ayrı yazılmıştı.
2. **2. tur, 2 bulgu (doğrulanıp düzeltildi):** panel tam gövde gönderdiği için "değişmemiş" bağlayıcı alan bayat kopyaydı ve CAS'sız yazılıp araya giren güncellemeyi sessizce geri alabiliyordu → okunan değerle aynı gelen bağlayıcı alanlar artık yazılmıyor; açık `category: null` doğrulamadan kaçıyordu → artık 400.
3. **3. tur: temiz** ("kalan hata yok").

## Sonuç
- Backend testleri 443/443 yeşil; tip kontrolünde yeni hata yok.
- Kod reposu commit'leri: `47295c8` (düzeltme), `ec45492` (1. tur bulguları), `c6f81fb` (2. tur bulguları). `main`'e fast-forward alındı; kurucu push'ladı (`origin/main = c6f81fb`).
- Panelde değişiklik gerekmedi.

## İlgili notlar
- [[2026-07-29 Kategori bazlı 3D üretim stratejisi — halı düz yüzey, mobilya Tripo devam, perde sonraya]] (kalınlık kuralının kaynağı: MIN_THICKNESS_MM = 1 mm)
- [[Seller Experience]] · [[Known Pitfalls]] · [[Current State]]
