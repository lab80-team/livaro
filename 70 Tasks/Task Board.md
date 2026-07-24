---
type: tasks
status: living
updated: 2026-07-24
---

# Task Board

> Standart Obsidian görev işareti kullanılır. Owner / alan / kaynak / due yalnızca **biliniyorsa** yazılır — uydurulmaz.
> Format: `- [ ] Görev — owner:: · area:: · source:: kaynak-linki · due::`

## Inbox
- [ ] Texture "Yeniden üret" butonu — area:: engineering · source:: `PROJECT_STATUS.md`
- [ ] RoomPlan yanlış algıları (TV=pencere) için kullanıcıya düzeltme imkânı değerlendir — area:: product · source:: [[2026-07-20 Oturum Import — Texture Pipeline ve Yakın Çekim]]

## Next
- [ ] Backend'i kurucu Mac'inden buluta taşı (arka plan render + bildirim ön şartı; gereksinim listesi kod reposunda README'de) — area:: engineering · source:: [[2026-07-24 PM önerileri kararları — bulut taşınma, kalite çıtası, bütçe rozeti]]
- [ ] Edge function'ı deploy et: `deno check` + Supabase secret'ları (R2_* 5 adet + APP_JWT_*) + TestFlight'ta katalog/auth/360° doğrula — area:: engineering · source:: [[2026-07-24 Oturum Import — Mimari Overhaul Fleet]]
- [ ] Blender USDZ'nin QuickLook'ta materyallerle açıldığını cihazda kontrol et (doğrulama turunun tek kalan maddesi) — area:: engineering · source:: [[2026-07-24 Oturum Import — Mimari Overhaul Fleet]]
- [ ] `drop_splat_and_ai_task` migration'ını uygula (`npx prisma migrate deploy`; splat_captures'ta silinecek 6 satır) — area:: engineering · source:: [[2026-07-24 Oturum Import — Mimari Overhaul Fleet]]
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
_(boş)_

## Blocked
_(boş)_

## Waiting
_(boş)_

## Done
- [x] Cihaz doğrulama turu (24 Tem): 360°/AR butonu ✓ (ilk kez çalışıyor), tarama + too-close ✓, yakın çekim texture akışı uçtan uca ✓ (floor.jpg gerçek parke fotoğrafından kırpıldı, R2+manifest doğrulandı), Yeniden Tasarla → yeni sahne ✓, Render gerçek odayla ✓ (girintili floorPolygon + kapı/pencere kesimleri doğru), AR relocalization ✓. Kalan: USDZ/QuickLook kontrolü (Next'te) — source:: [[2026-07-24 Oturum Import — Mimari Overhaul Fleet]]
- [x] Yakın çekim texture akışını cihazda uçtan uca doğrula — 24 Tem turunda doğrulandı (yukarıda) — source:: [[2026-07-19 Tarama akışına zemin-duvar yakın çekim adımları]]
- [x] Faz 3 gerçek-veri testi: girintili odada `floorPolygon` zincirleme — 24 Tem render'ında gerçek girintili odada doğru çalıştı — source:: `PROJECT_STATUS.md`
- [x] Faz 3 gerçek-veri testi: kapı/pencere boolean kesimleri — 24 Tem render'ında gerçek duvarlarda doğru çıktı — source:: `PROJECT_STATUS.md`
- [x] Eski gpt-image-1 render yolunun akıbetine karar ver — yol 21 Tem temizliğinde söküldü, 24 Tem overhaul'unda doğrulandı; karar gerekmiyor (geri dönüş: `pre-cleanup-2026-07-21` tag'i) — source:: [[2026-07-24 Oturum Import — Mimari Overhaul Fleet]]
- [x] Oda tarama deney sonuçlarını [[Experiment Index]]'e ekle — source:: [[2026-07-19 Proje Kurulum Brief]] (oturum import'larıyla tamamlandı, 2026-07-20)
