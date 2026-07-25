---
type: import
date: 2026-07-24
status: processed
---

# Oturum Import — Mimari Overhaul (iki-mimar fleet + Codex)

> Kaynak: 24 Tem Claude Code oturumu. Kurucu talebi: vault'taki güncel kararlara göre kod tabanını iki senior software architect ajanıyla (tartışmalı fleet) elden geçirmek. Bu not oturumun özet kaydıdır; ayrıntı kod reposunda (`cleanup/dead-code` branch'i, 7 commit + `PROJECT_STATUS.md`).

## Süreç

1. Vault sindirildi (24 Tem teyit turu dahil tüm kararlar) → fleet brief'i yazıldı.
2. İki mimar ajan bağımsız değerlendirme yaptı (backend merceği / iOS merceği), sonra birbirinin bulgularını kod üzerinde doğrulayıp tartıştı; ihtilaflar çözüldü (ör. "reconcile seam" önerisi "tek adapter = hipotetik seam" ilkesiyle geri çekildi).
3. Uzlaşılan plan iki lane'de uygulandı; her adımda kapılar: `tsc` + jest + `xcodebuild`.
4. Codex CLI incelemesi 6 bulgu verdi (2'si ciddi güvenlik); hepsi düzeltildi; ikinci Codex geçişiyle doğrulandı.

## Kod tabanında yapılanlar (7 commit, `cleanup/dead-code`)

- **Bekleyen işler güvenceye alındı**: RLS migration (23 Tem'de uygulanmıştı, commit'siz duruyordu), Release build'in Supabase edge function aynasına bağlanması (`APIConfig` DEBUG/RELEASE), AppIcon, ExportOptions.
- **Söküm**: backend `order` + `user` modülleri (üç istemcide de çağıran yok; checkout-yok kararıyla da çelişiyordu); iOS'ta ControlNet kalıntısı SceneSnapshotBridge + hiç veri üretmeyen coverage/mesh istatistik makinesi (canlı `checkTooClose` uyarısı korundu).
- **Güvenlik**: kayıt artık yalnız CUSTOMER üretir (SELLER hesapları elle açılır — [[2026-06-22 iOS uygulaması yalnızca müşteri tarafı]] ile uyumlu); `presignUrl` keyfî URL imzalama açığı kapatıldı (yalnız R2 prefix'i); 3d-pipeline okumaları satıcının kendi markasına daraltıldı; design-result oluşturma tarama sahipliğini doğruluyor.
- **Presign kontratı**: ürün/3D model URL'leri artık her yüzeyde (Nest + edge) imzalı — ürün detayındaki "360°/AR'da Gör" ilk kez çalışır durumda (cihaz doğrulaması bekliyor).
- **Yapı**: RoomScene3DView 839→467 satır (render galerisi ayrı dosyaya); depolama servisleri amaç-adlı ayrıldı (Supabase public görsel vs R2 presigned 3D); "Yeniden Tasarla" sonrası bayat sahne düzeltildi.
- **Test**: backend 21→39 (texture pipeline karakterizasyon testleri dahil — [[Known Pitfalls]]'taki iki sessiz regresyon bölgesi artık testle dondurulmuş); iOS 53→62 (backend-JSON decode fikstürleri).

## Tespit edilen karar-kod boşlukları (yapılMADI — bilinçli; özellik işi)

- Sepet "pasif liste" henüz kodda yok (placeholder sekme) → [[2026-07-24 Sepet MVP'de, checkout ödeme teknolojisi seçilince]]
- "Yeniden tasarla 2 hak" sayacı yok → [[2026-07-24 MVP tasarım kapsamı — oda boşaltılır, sıfırdan tasarım]]
- Wizard'da "AI özet + onay" adımı yok
- %20 bütçe aşım tavanı kodda yok (lineer yumuşak çürüme var, sert tavan yok) → [[2026-07-24 Bütçe aşım tavanı yüzde 10]]
- Render bildirimi yok (5 sn polling) → [[2026-07-24 Anlık deneyim — canlı 3D sahne, render arka planda]]
- "GLB min-oran fit" ifadesi kodla uyuşmuyor (kod eksen-bazlı tam ölçek uyguluyor) — Needs Validation

## Dışarıda kalan işler (deploy/cihaz) — güncelleme: aynı gün kapatıldı

- ~~Edge function deploy'u~~ — **YAPILDI (aynı gün)**: 5 R2 secret'ı yüklendi, function deploy edildi; canlı doğrulama: katalog 200 + usdzUrl imzalı ve indirilebilir (HTTP 206), yanlış login 401 (verify_jwt=false handler'a ulaştırıyor), kısa şifre register 400. **Release build telefonda da doğrulandı** (katalog + 360°/AR + giriş 3/3 ✓; Release config doğrudan kuruldu — TestFlight ile aynı kod yolu; test sonrası Debug geri kuruldu). Gerçek TestFlight yüklemesi dağıtım gerektiğinde yapılacak.
- ~~Cihaz doğrulama turu~~ — **YAPILDI (aynı gün, 7/7)** — yukarıdaki bölüm.
- `drop_splat_and_ai_task` migration'ı hâlâ uygulanmadı (24 Tem'de DB'den doğrulandı).
- **İlk TestFlight yüklemesi — YAPILDI (25 Tem)**: build 1.0 (2026072401) App Store Connect'e yüklendi. İlk deneme Apple 90474 hatasıyla döndü (iPad + salt-dikey); çözüm `TARGETED_DEVICE_FAMILY=1` (iPhone-only — [[2026-07-24 MVP yalnızca LiDAR'lı iPhone]] kararıyla uyumlu). Sürümleme artık project.yml `info.properties`'te (tarih bazlı build no).

## Cihaz doğrulama turu sonuçları (aynı gün, kurucu telefonda)

- **360°/AR butonu ✓** — presign düzeltmesiyle İLK KEZ çalıştı.
- **Tarama + too-close uyarısı ✓** — coverage sökümü regresyon yaratmadı.
- **Yakın çekim texture akışı uçtan uca ✓** — scan `be15108e…`: R2'de 4 köşe foto + src_floor/src_wall + walls/floor/manifest; `floor.jpg`'nin zemin yakın çekiminden kırpıldığı görsel karşılaştırmayla kanıtlandı; manifest alanları sözleşmeye birebir uygun.
- **Yeniden Tasarla ✓** — dönüşte yeni sahne görünüyor (bugünkü düzeltme çalışıyor).
- **Render gerçek odayla ✓** — girintili odada floorPolygon doğru; kapı/pencere kesimleri doğru; gerçek parke dokusu zeminde.
- **AR relocalization ✓** — mobilyalar gerçek odanın zeminine oturuyor.
- **Blender USDZ QuickLook'ta materyallerle açıldı ✓** (parke dokusu, duvar rengi, kapı/pencere panelleri) — tur 7/7 tamamlandı.
- **Gözlemler (yeni işler doğurdu → [[Task Board]])**: (1) karo tekrarında ışık farkı ızgara deseni; (2) bir Tripo modelinde ölçek/yerleşim tuhaflığı (GPT-4o yerleşim testi + Tripo ölçek/rotasyon doğrulamasının önemi arttı); (3) RoomScan `createdAt` 3 saat geride (saat dilimi tuhaflığı).

## İşlendiği notlar

[[Current State]], [[System Architecture]], [[Known Pitfalls]], [[E2E Testing Strategy]], [[60 Planning/Technical Plan|Technical Plan]], [[Open Questions]], [[Task Board]]
