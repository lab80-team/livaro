---
type: knowledge
status: draft
updated: 2026-07-20
related: []
---

# E2E Testing Strategy

## Şu An Bilinenler
- Resmî/otomatik test stratejisi **yok**; fiilî doğrulama pratiği (7-20 Tem oturumlarından):
  - Derleme kapıları: `npx tsc --noEmit` (backend) + `xcodebuild … CODE_SIGNING_ALLOWED=NO` (iOS).
  - Cihazda manuel uçtan uca test (tarama → foto → texture → tasarım → render), backend log + R2 içeriği kontrolüyle.
  - Modal'da sabit **4×5 m test odası** render'ı (pencere/kapılı) — pipeline değişikliklerinde smoke test.
  - Scratchpad script'leriyle birim benzeri kontroller (örn. `cropMirrorTile` karo sürekliliği).
- Ders: texture pipeline'da iki kez sessiz regresyon yaşandı — görsel çıktı doğrulaması (R2'deki dosya içeriği + log satırları) şart. Bkz. [[Known Pitfalls]].

## Varsayımlar
- Prototip fazında manuel + smoke test yeterli; kullanıcı testi öncesi kritik akışlara otomasyon gerekecek — **Needs Validation**.

## Bilinmeyenler
- Test araçları, kapsam, CI — **To Be Decided**.
- Render kalitesinin (texture doğruluğu) otomatik ölçümü — **Unknown** (fikir: renk histogram karşılaştırması — öneri, karar değil).

## Önemli Sorular
- İlk otomasyon nereye: texture üretim zinciri mi, tarama→kayıt API'si mi?

## İlgili Notlar
- [[60 Planning/Product Flows|Product Flows]], [[System Architecture]], [[Known Pitfalls]], [[Experiment Index]]

## Kaynaklar
- [[2026-07-20 Oturum Import — Texture Pipeline ve Yakın Çekim]]
