---
type: knowledge
status: living
updated: 2026-07-31
related: []
---

# System Architecture

> Kaynaklar: kod reposundaki `PROJECT_STATUS.md` (16 Tem) + oturum import'ları. Kod reposu: `~/Desktop/livaro` (GitHub: lab80-team).

## Şu An Bilinenler

### Yığın (Stack)
- **iOS uygulaması** (Swift/SwiftUI, iOS 17+, sıfır 3. parti bağımlılık, Swift 6 strict concurrency): **yalnızca müşteri (CUSTOMER) tarafı** — bkz. [[2026-06-22 iOS uygulaması yalnızca müşteri tarafı]]. LiDAR'lı iPhone hedefli. RoomPlan (tarama), ARKit, RealityKit (3D sahne), QuickLook (USDZ), AVCapturePhoto (köşe fotoğrafları). Proje `xcodegen` ile üretilir (`project.yml` → pbxproj). (MetalSplatter/splat viewer 21 Tem temizliğinde söküldü; geri dönüş `pre-cleanup-2026-07-21` tag'i.)
- **web/** (mağaza sitesi) + **admin/** (yönetim sitesi) — 2026-07-29'da build edilen, main'e 2026-07-31'de birleştirilmiş (`44a4497`) iki ayrı yeni site: kayıt→admin onayı→giriş→ürün+4 etiketli foto→3D→mağaza onayı→admin onayı→katalog zinciri. Vite + React Router + Tailwind v4; aynı "Sıcak/Lüks" görsel kimlik. Detay: [[Seller Experience]].
- **brand-panel** (eski web paneli, `brand-panel/` alt dizini): Haziran'dan kalma ilk satıcı paneli — ürün yükleme (4 açı fotoğrafı → Tripo3D). Temmuz oturumlarında dokunulmadı, `web/` build'inde de referans dışında dokunulmadı; güncel durumu **Needs Validation**. Emekliye ayrılma kararı henüz verilmedi.
- **Backend**: NestJS + Prisma (adapter-pg) + PostgreSQL (Supabase pooler). BullMQ/Redis (Upstash kotası nedeniyle dev'de yerel Redis). JWT auth (passport-jwt). Modüller (24 Tem overhaul sonrası): auth, product, brand, fabric, room-scan, three-d-pipeline, ai-designer, design-result, embedding, storage, redis, prisma (+ `/api/health`). `order` ve `user` modülleri söküldü (çağıransız; checkout MVP'de yok).
- **Supabase Edge Function aynası** (`supabase/functions/api`, Deno): Release iOS build'inin bağlandığı katalog + auth aynası; oda tarama / AI tasarım 501 döner. `config.toml` `verify_jwt=false` (auth handler içinde). Nest buluta çıkınca kaderi kararlaştırılacak.
- **Depolama**: Cloudflare R2 (bucket `three-d-models`, **public değil** — iOS'a giden her URL presigned olmak zorunda). Kontrat (24 Tem): ham R2 URL DB'de kalır, imza her zaman serialization sınırında (`R2StorageService.presignModelUrls`); `presignUrl` yalnız `R2_PUBLIC_URL` prefix'li URL'leri imzalar (keyfî-URL imzalama açığı kapatıldı). Ürün görselleri ayrı: `ProductImageStorageService` (Supabase public bucket).
- **Güvenlik duruşu (23-24 Tem)**: DB'de RLS deny-by-default (migration commit'li); kayıt yalnız CUSTOMER üretir (SELLER elle açılır); 3d-pipeline okumaları SELLER'da kendi markasıyla sınırlı; design-result oluşturma tarama sahipliğini doğrular (bilgi sızdırmayan 404'ler).
- **GPU / render**: Modal — `blender/modal_blender.py` (headless Blender 4.2, Cycles, T4) ve `gsplat/modal_app.py` (rafta). Bkz. [[2026-07-11 GPU sağlayıcısı Modal]].
- **AI servisleri**: OpenAI GPT-4o (materyal analizi `analyzeRoomPhotos`, oda kimliği `analyzeRoomIdentity`, AI Designer yerleşimi, embedding) + gpt-image-1 (eski render yolu); Replicate flux-schnell (texture fallback + render güzelleştirme `_enhance_render`); Tripo3D (**kategoriye göre**: mobilya `multiview_to_model` 4 açı, model sürümü v3.1; halı Tripo KULLANMIYOR — Tripo'suz düz yüzey + yüksek çözünürlüklü doku yolu; perde tedarik yolu henüz seçilmedi → [[2026-07-29 Kategori bazlı 3D üretim stratejisi — halı düz yüzey, mobilya Tripo devam, perde sonraya]]); eski `/3d-pipeline` HTTP uç katmanı 2026-07-31'de tamamen kaldırıldı (kullanılmıyordu; motor kendisi `seller-products`/`admin` uçlarından çağrılıyor) → [[2026-07-31 Kullanılmayan 3d-pipeline HTTP uçları tamamen kaldırıldı]]; pgvector (semantik ürün arama).
- **AI Designer motoru** (Faz 4, Haziran): GPT-4o Türkçe istek parse + text-embedding-3-small + pgvector cosine arama; bütçe yumuşak tercih / oda ölçüsü sert filtre (SIMILARITY_WEIGHT=0.7, BUDGET_WEIGHT=0.3, ROOM_FIT_RATIO=0.6) — bkz. [[2026-06-20 Bütçe yumuşak tercih]]. Senkron `POST /ai/designer/search`.

### Aktif akış (20 Tem itibarıyla)
```
TARAMA:  RoomPlan (yalnızca o) → Bitir → RoomPhotoCaptureView (4-8 köşe foto;
         planda: + zemin/duvar yakın çekim, isteğe bağlı)
KAYIT:   POST room-scans → analyze-materials (GPT-4o) → generate-textures
         (fotoğraftan kırpma + mirror tile; fallback GPT bölge → flux) → R2
         room-textures/{scanId}/ (walls.jpg, floor.jpg, manifest.json, src_i.jpg)
TASARIM: AI Designer wizard → pgvector ürün arama + GPT-4o yerleşim →
         design_results (placedProducts JSON) → RoomScene3DView'da kutu→usdz değişimi
RENDER:  POST /design-results/:id/render-blender → Modal Blender → 4× PNG (2048)
         + room.glb + room.usdz → R2 blender-rooms/{designId}/ → iOS 5sn polling
         → galeri + USDZ QuickLook
```

### Önemli dosyalar (24 Tem overhaul sonrası)
- iOS: `Rooms/RoomCaptureRepresentable.swift`, `Rooms/RoomPhotoCaptureView.swift`, `Rooms/RoomCaptureFlowView.swift`, `Scene3D/RoomScene3DView.swift` (3D + Kat Planı), `Scene3D/RenderGalleryView.swift` (render galerisi + QuickLook), `Scene3D/RoomSceneBuilder.swift`, `Rooms/RoomTextureCache.swift`, `Networking/LivaroAPI.swift` + `APIConfig.swift` (DEBUG=mDNS, RELEASE=edge)
- Backend: `src/room-scan/` (analiz + TexturePipelineService + ReplicateService), `src/design-result/` (render-blender + BlenderService), `src/ai-designer/`, `src/storage/` (r2-storage + product-image-storage), `supabase/functions/api/` (edge aynası)
- Modal: `blender/modal_blender.py`, `blender/room_to_blender.py` (bpy; ARKit Y-up → Blender Z-up)
- Prisma: RoomScan (data JSON: geometri), DesignResult, Product, ThreeDModel (usdzUrl/glbUrl). (`drop_splat_and_ai_task` migration'ı hâlâ uygulanmadı — 24 Tem'de DB'den doğrulandı.)

### Ölçek / birimler
- Oda geometrisi uçtan uca **gerçek metre** (1 Blender birimi = 1 m; USDZ metersPerUnit=1). Oda hiçbir yerde küçültülmüyor (17 Tem soruşturmasıyla doğrulandı).
- **DÜZELTME (2026-07-31, kod incelemesi):** Bu not daha önce burada mobilya GLB'lerinin ürünün cm ölçülerine "min-oran uniform fit" ile ölçeklendiğini söylüyordu — bu **yanlıştı**. Kod (`ModelLoader.swift`) her eksende (x/y/z) **ayrı ayrı** gerilme (non-uniform stretch) yapıyor: `loaded.scale = [size.x/ext.x, size.y/ext.y, size.z/ext.z]`. Yani GLB'nin kendi en-boy oranı üründen farklıysa mobilya "iki eksende küçük" kalmıyor, üç eksende de hedef kutuya tam oturacak şekilde gerilip distorte oluyor (bilinen zayıflık, farklı türden). `widthCm` boşsa hiç ölçeklenmez.

## Varsayımlar
- Modal + R2 + yerel backend kombinasyonu prototip fazı için yeterli — production mimarisi ayrıca tasarlanacak (**To Be Decided**).

## Bilinmeyenler
- Production deployment (backend nerede koşacak, auth/ödeme, App Store süreci) — **Unknown**. Bkz. [[Deployment Strategy]].
- Tripo GLB rotasyon işareti (ARKit rotY ↔ Blender Z) doğrulanmadı — **Needs Validation**.

## Önemli Sorular
- Render maliyeti/süresi ölçekte ne olur (Modal T4 ~2-3 dk/render)?
- Texture pipeline'ın kalite güvencesi nasıl otomatikleştirilir (regresyonlar yaşandı)?

## İlgili Notlar
[[3D Render Pipeline]], [[Room Scanning Overview]], [[Known Pitfalls]], [[Deployment Strategy]]

## Kaynaklar
- `~/Desktop/livaro/PROJECT_STATUS.md` (16 Tem, birinci elden özet)
- [[2026-07-16 Oturum Import — 3D Pipeline Evrimi]], [[2026-07-20 Oturum Import — Texture Pipeline ve Yakın Çekim]]
- [[2026-07-29 Build Oturumu — Mağaza Web ve Yönetim Sitesi]], [[2026-07-31 Kategori 3D Stratejisi, Tripo Kredi Ölçümü, iOS Doku Düzeltmesi ve Main Merge]]
