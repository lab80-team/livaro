---
type: planning
status: living
updated: 2026-07-20
---

# Technical Plan

> Teknik yol haritası. İçerik kararlar/deneyler netleştikçe güncellenir. Mevcut mimari: [[System Architecture]].

## Şu Anki Durum
- **Aktif teknik yol** (16 Tem'den beri): RoomPlan geometri + fotoğraftan texture + Modal'da Blender render/USDZ. Bkz. [[3D Render Pipeline]], [[Blender mimari render Modal]].
- Onaylı son iş: tarama akışına zemin/duvar yakın çekim adımları ([[2026-07-19 Tarama akışına zemin-duvar yakın çekim adımları]]) — push edildi, cihaz doğrulaması bekliyor.

## Sıradaki Teknik İşler (kaynak: PROJECT_STATUS.md + 17-20 Tem oturumu)
1. **Faz 3 gerçek-veri testi**: girintili odada `floorPolygon`; Tripo GLB ölçek/rotasyon işareti; Blender USDZ'nin QuickLook materyel uyumu; eğik duvarlarda kapı/pencere boolean kesimleri.
2. **Yakın çekim akışının uçtan uca doğrulaması** (cihazda; Nest log "yakın çekimden kırpıldı [floor]" + USDZ'de birebir doku; atla senaryosunda GPT bölge yolu).
3. **Katalog**: DB'de yalnızca 3 usdz'li test ürünü var (18 ürün bilinçli silindi, 15 Tem). Gerçek katalog ürünleri ekle + Tripo3D pipeline'ından toplu geçir — tasarım çeşitliliğinin ön koşulu.
4. Opsiyonel: Blender çıktısını img2img ile fotogerçekçileştirme katmanı (mevcut `_enhance_render`).
5. Açık: eski gpt-image-1 render yolunun akıbeti; `coverageGateEnabled` bayrağı; texture "Yeniden üret" butonu; ARKit mesh'i geri açma kararı; gsplat'a dönüş (rafta).

## Bayraklar / rafta bekleyenler
- `arkitMeshEnabled=false` (ARKit mesh offline), `USE_COLMAP=true` (gsplat, rafta), `coverageGateEnabled=false`.

## Açık Teknik Kararlar
- Production deployment (hosting, TestFlight, CI/CD) — bkz. [[Deployment Strategy]]
- LiDAR'sız cihaz stratejisi — bkz. [[Room Scanning Overview]]
- Test yaklaşımı — bkz. [[E2E Testing Strategy]]

## İlgili Notlar
- [[Roadmap]]
- [[System Architecture]]
- [[Known Pitfalls]]
- [[Launch Checklist]]
