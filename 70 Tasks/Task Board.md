---
type: tasks
status: living
updated: 2026-08-05
---

# Task Board

> Standart Obsidian görev işareti kullanılır. Owner / alan / kaynak / due yalnızca **biliniyorsa** yazılır — uydurulmaz.
> Format: `- [ ] Görev — owner:: · area:: · source:: kaynak-linki · due::`

## Inbox
- [ ] Texture "Yeniden üret" butonu — area:: engineering · source:: `PROJECT_STATUS.md`
- [ ] RoomPlan yanlış algıları (TV=pencere) için kullanıcıya düzeltme imkânı değerlendir — area:: product · source:: [[2026-07-20 Oturum Import — Texture Pipeline ve Yakın Çekim]]

## Next
- [ ] Mobilyada Tripo ön/arka/sol/sağ eşlemesini gerçek 4 açılı bir ürünle doğrula (kredi harcar) — **pilottan önce** — area:: engineering · source:: [[2026-07-29 Kategori bazlı 3D üretim stratejisi — halı düz yüzey, mobilya Tripo devam, perde sonraya]]
- [ ] iOS'u Xcode'da derle ve test et (KVKK sızıntı düzeltmesi `Brand.swift`'te `ownerId` alanını opsiyonel yaptı, henüz doğrulanmadı) — area:: engineering · source:: [[2026-07-31 Kategori 3D Stratejisi, Tripo Kredi Ölçümü, iOS Doku Düzeltmesi ve Main Merge]]
- [ ] Perde tedarik yolunu seç (freelancer $500-1500/3-5 hafta vs hazır asset kütüphanesi; "kumaş değiştirilebilir UV" desteği doğrulanmalı) — area:: product/business · source:: [[2026-07-29 Kategori bazlı 3D üretim stratejisi — halı düz yüzey, mobilya Tripo devam, perde sonraya]]
- [ ] Kategori listesi + kategoriye özel soru setlerini hazırla (bir sonraki thinking session'ın ön hazırlığı; ürün formu ve Excel şablonu buna bağımlı) — owner:: Selim/Yusuf · area:: product · source:: [[2026 07 28 Thinking Session — Mağaza Web Paneli User Journey]]
- [ ] Backend'i kurucu Mac'inden buluta taşı (arka plan render + bildirim ön şartı; gereksinim listesi kod reposunda README'de) — area:: engineering · source:: [[2026-07-24 PM önerileri kararları — bulut taşınma, kalite çıtası, bütçe rozeti]]
- [ ] Birim maliyet analizini yap ve sonuçları vault'a aktar (kurucular kendisi yapacak) — owner:: Selim/Yusuf · area:: business · source:: [[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu]] (Bölüm 4)
- [ ] GPT-4o yerleşimini kapsamlı test et; sonuca göre teknoloji kararı (kural tabanlı sisteme geçiş dahil) — **sıralama (teyit turu): MVP altyapısı/3D model tamamlandıktan sonra** — area:: engineering/product · source:: [[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu]] (cevap 14 + Bölüm 3)
- [ ] İade/iptal kurallarının hukuki tanımını araştır (14 gün cayma hakkı + özel üretim istisnası + emanet/lisans sorusu) — area:: business/legal · source:: [[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu]] (cevap 25)
- [ ] Toplu ürün yükleme Excel şablonunu tasarla (fotoğraf bağlantısı çözümü dahil) — area:: product/engineering · source:: [[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu]] (cevap 16)
- [ ] Wizard tarz kartlarına fotoğraf ekle — area:: product/engineering · source:: [[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu]] (cevap 4)
- [ ] Pazarlık/hizmet bedeli stratejisi üzerine düşün (rafa mı, ne zaman, hangi kurallarla) — area:: business · source:: [[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu]] (cevap 21)
- [ ] Faz 3 gerçek-veri testi: Tripo GLB ölçek/rotasyon işareti doğrulaması — 24 Tem turunda görsel şüphe doğdu (bir modelde ölçek/yerleşim tuhaflığı; render'da koltuğa giriyor) — area:: engineering · source:: `PROJECT_STATUS.md` + [[2026-07-24 Oturum Import — Mimari Overhaul Fleet]]
- [ ] Texture karo tekrarındaki aydınlık leke deseni (kırpılan fotoğrafın ışık farkı ızgara gibi tekrarlıyor) kabul edilebilir mi — değerlendir — area:: product/engineering · source:: [[2026-07-24 Oturum Import — Mimari Overhaul Fleet]]
- [ ] RoomScan `createdAt` damgası dosya saatlerinden 3 saat geride (saat dilimi tuhaflığı) — kaynağını bul — area:: engineering · source:: [[2026-07-24 Oturum Import — Mimari Overhaul Fleet]]
- [ ] Katalog: gerçek ürünleri ekle + Tripo3D pipeline'ından toplu geçir (şu an 3 test ürünü) — area:: product/engineering · source:: `PROJECT_STATUS.md`

## In Progress
- [ ] **2026-08-05 kararlarının 6 görevi KODLANDI, main'e merge bekliyor** (`feature/store-panel-3d-progress` branch'i, 6 commit; 431 test yeşil; canlı demo yerelde yapıldı 2026-08-05): süre ölçümü + yüzde kaydı, hafif ilerleme ucu + her sayfada kapatılabilir kutucuk, sistem hatasında hak iadesi (aynı fotoğrafla tekrar), stok göstergesi + 5 yayın filtresine stok koşulu, 3D model + onayın düzenleme sayfasına taşınması. Kalan: Codex inceleme kapısı → merge; Supabase aynasının deploy'u ayrı karar — area:: engineering · source:: [[2026 08 05 Thinking Session — Mağaza Paneli 3D İlerleme ve Stok Göstergesi]]

## Blocked
_(boş)_

## Waiting
_(boş)_

## Done
- [x] AI aramada oda taraması sahiplik kontrolü eklendi (2026-08-02): yabancı/olmayan `roomScanId` → bilgi sızdırmayan 404, sahiplik geçmeden OpenAI çağrısı yok; main'e merge + push (`0477596`), 6 tur Codex incelemesi — source:: [[2026-08-02 Güvenlik Düzeltmeleri — Oda Taraması Sahipliği ve Render Kilidi]]
- [x] Blender render mükerrer tetikleme koruması atomik yapıldı (2026-08-02): `renderClaimedAt` CAS kilidi + fence + 3 dk spawn zaman aşımı + belirsiz-start koruması; migration uygulandı — source:: [[2026-08-02 Güvenlik Düzeltmeleri — Oda Taraması Sahipliği ve Render Kilidi]]
- [x] `drop_splat_and_ai_task` migration'ını uygula — bayatlamış görev: `prisma migrate status` (2026-08-02) 13 migration'ın tamamının uygulandığını, şemanın senkron olduğunu doğruladı (ne zaman uygulandığı kayıtlı değil) — source:: [[2026-08-02 Güvenlik Düzeltmeleri — Oda Taraması Sahipliği ve Render Kilidi]]
- [x] Release build'inde edge yolu uygulama içinden doğrulandı (24 Tem): katalog ✓, 360°/AR ✓, giriş ✓ (Release config doğrudan cihaza kuruldu — TestFlight kullanıcısıyla aynı kod yolu; tarama/AI tasarım bilinçli 501). Test sonrası Debug build geri kuruldu — source:: [[2026-07-24 Oturum Import — Mimari Overhaul Fleet]]
- [x] Edge function deploy'u (24 Tem): 5 R2 secret'ı yüklendi (APP_JWT_* zaten vardı), function deploy edildi, canlıda doğrulandı — katalog 200 + usdzUrl imzalı ve indirilebilir (206), yanlış login 401 (verify_jwt=false çalışıyor), kısa şifre register 400 (yeni doğrulama) — source:: [[2026-07-24 Oturum Import — Mimari Overhaul Fleet]]
- [x] Cihaz doğrulama turu (24 Tem): 360°/AR butonu ✓ (ilk kez çalışıyor), tarama + too-close ✓, yakın çekim texture akışı uçtan uca ✓ (floor.jpg gerçek parke fotoğrafından kırpıldı, R2+manifest doğrulandı), Yeniden Tasarla → yeni sahne ✓, Render gerçek odayla ✓ (girintili floorPolygon + kapı/pencere kesimleri doğru), AR relocalization ✓, Blender USDZ QuickLook'ta materyallerle açıldı ✓ — TUR TAMAMLANDI (7/7) — source:: [[2026-07-24 Oturum Import — Mimari Overhaul Fleet]]
- [x] Yakın çekim texture akışını cihazda uçtan uca doğrula — 24 Tem turunda doğrulandı (yukarıda) — source:: [[2026-07-19 Tarama akışına zemin-duvar yakın çekim adımları]]
- [x] Faz 3 gerçek-veri testi: girintili odada `floorPolygon` zincirleme — 24 Tem render'ında gerçek girintili odada doğru çalıştı — source:: `PROJECT_STATUS.md`
- [x] Faz 3 gerçek-veri testi: kapı/pencere boolean kesimleri — 24 Tem render'ında gerçek duvarlarda doğru çıktı — source:: `PROJECT_STATUS.md`
- [x] Eski gpt-image-1 render yolunun akıbetine karar ver — yol 21 Tem temizliğinde söküldü, 24 Tem overhaul'unda doğrulandı; karar gerekmiyor (geri dönüş: `pre-cleanup-2026-07-21` tag'i) — source:: [[2026-07-24 Oturum Import — Mimari Overhaul Fleet]]
- [x] Oda tarama deney sonuçlarını [[Experiment Index]]'e ekle — source:: [[2026-07-19 Proje Kurulum Brief]] (oturum import'larıyla tamamlandı, 2026-07-20)
