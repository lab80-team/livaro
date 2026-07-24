---
type: knowledge
status: living
updated: 2026-07-24
related: []
---

# E2E Testing Strategy

## Şu An Bilinenler
- **Otomatik test tabanı var (24 Tem overhaul'dan beri)**:
  - Backend: jest **39 test / 11 suite** — texture pipeline karakterizasyonu (walls/floor kontratı, manifest alanları, presigned textureUrl, R2 anahtar düzeni, yakın çekim → köşe foto → flux fallback sırası; ağ mock, görüntü işleme gerçek), R2 presign allowlist, 3d-pipeline/design-result sahiplik guard'ları, geometri/yerleşim birim testleri.
  - iOS: **62 test** — backend-JSON decode fikstürleri (Page/Product, AIDesignerSearchResponse, DesignResult, RoomTexturesResponse zorunlu alanlar, BlenderRenderState) + mevcut birim testleri.
- Derleme kapıları: `npx tsc --noEmit` (backend; supabase/ Deno dosyası hariç) + `xcodebuild … CODE_SIGNING_ALLOWED=NO` (iOS).
- Hâlâ manuel olanlar: cihazda uçtan uca akış (tarama → foto → texture → tasarım → render), backend log + R2 içerik kontrolü; Modal'da sabit **4×5 m test odası** smoke render'ı.
- Ders: texture pipeline'da iki kez sessiz regresyon yaşandı — kontrat artık karakterizasyon testleriyle donduruldu; görsel çıktı doğrulaması (R2 içerik) hâlâ manuel. Bkz. [[Known Pitfalls]].

## Varsayımlar
- Prototip fazında manuel + smoke test yeterli; kullanıcı testi öncesi kritik akışlara otomasyon gerekecek — **Needs Validation**.

## Bilinmeyenler
- Test araçları, kapsam, CI — **To Be Decided**.
- Render kalitesinin (texture doğruluğu) otomatik ölçümü — **Unknown** (fikir: renk histogram karşılaştırması — öneri, karar değil).

## Önemli Sorular
- ~~İlk otomasyon nereye?~~ **Fiilen cevaplandı (2026-07-24)**: texture üretim zinciri karakterizasyon testleriyle donduruldu; tarama→kayıt API'sinin sahiplik guard'ları da testli.
- Cihaz gerektiren akışlar (tarama, AR, QuickLook) için otomasyon mümkün mü, değer mi? — **To Be Decided**.

## İlgili Notlar
- [[60 Planning/Product Flows|Product Flows]], [[System Architecture]], [[Known Pitfalls]], [[Experiment Index]]

## Kaynaklar
- [[2026-07-20 Oturum Import — Texture Pipeline ve Yakın Çekim]]
