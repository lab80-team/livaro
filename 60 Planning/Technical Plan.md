---
type: planning
status: living
updated: 2026-07-24
---

# Technical Plan

> Teknik yol haritası. İçerik kararlar/deneyler netleştikçe güncellenir. Mevcut mimari: [[System Architecture]].

## Şu Anki Durum
- **Aktif teknik yol** (16 Tem'den beri): RoomPlan geometri + fotoğraftan texture + Modal'da Blender render/USDZ. Bkz. [[3D Render Pipeline]], [[Blender mimari render Modal]].
- **Mimari overhaul yapıldı (2026-07-24)**: ölü modüller söküldü, güvenlik sıkılaştırıldı, presign kontratı her yüzeyde, test sayısı backend 39 / iOS 62 → [[2026-07-24 Oturum Import — Mimari Overhaul Fleet]]. Commit'ler `cleanup/dead-code` branch'inde (push edilmedi).
- Onaylı son iş: tarama akışına zemin/duvar yakın çekim adımları ([[2026-07-19 Tarama akışına zemin-duvar yakın çekim adımları]]) — push edildi, cihaz doğrulaması bekliyor.

## Sıradaki Teknik İşler (kaynak: PROJECT_STATUS.md + 17-20 Tem oturumu)
1. **Faz 3 gerçek-veri testi**: girintili odada `floorPolygon`; Tripo GLB ölçek/rotasyon işareti; Blender USDZ'nin QuickLook materyel uyumu; eğik duvarlarda kapı/pencere boolean kesimleri.
2. **Yakın çekim akışının uçtan uca doğrulaması** (cihazda; Nest log "yakın çekimden kırpıldı [floor]" + USDZ'de birebir doku; atla senaryosunda GPT bölge yolu).
3. **Katalog**: DB'de yalnızca 3 usdz'li test ürünü var (18 ürün bilinçli silindi, 15 Tem). Gerçek katalog ürünleri ekle + Tripo3D pipeline'ından toplu geçir — tasarım çeşitliliğinin ön koşulu.
4. **Edge function deploy'u** (24 Tem overhaul çıktısı): `deno check` + Supabase secret'ları (R2_* 5 adet + APP_JWT_*) + TestFlight'ta katalog/auth/360° doğrulaması.
5. **Cihaz doğrulama turu** (overhaul sonrası): tarama + too-close, "Yeniden Tasarla" → yeni sahne, ProductDetail 360°/AR, Render sekmesi, AR relocalization.
6. Opsiyonel: Blender çıktısını img2img ile fotogerçekçileştirme katmanı (mevcut `_enhance_render`).
7. Açık: texture "Yeniden üret" butonu; ARKit mesh'i geri açma kararı; gsplat'a dönüş. (gpt-image-1 yolu ve `coverageGateEnabled` bayrağı 21+24 Tem temizlikleriyle kod tabanından çıktı — karar gerekmiyor.)

## Bayraklar / rafta bekleyenler
- Eski bayraklar (`arkitMeshEnabled`, `USE_COLMAP`, `coverageGateEnabled`) 21+24 Tem temizlikleriyle kodla birlikte söküldü; geri dönüş noktası: `pre-cleanup-2026-07-21` git tag'i.

## Açık Teknik Kararlar
- Production deployment (hosting, TestFlight, CI/CD) — bkz. [[Deployment Strategy]]
- LiDAR'sız cihaz stratejisi — bkz. [[Room Scanning Overview]]
- Test yaklaşımı — bkz. [[E2E Testing Strategy]]

## İlgili Notlar
- [[Roadmap]]
- [[System Architecture]]
- [[Known Pitfalls]]
- [[Launch Checklist]]
