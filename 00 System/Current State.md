---
type: system
status: living
updated: 2026-07-20
---

# Current State

> Projenin **şu anki** özeti. Sürekli güncellenir. **Tarihçe tutulmaz** — geçmiş, kaynak notlarda ([[Meeting Index]], Inbox import'ları) ve Git'te.
>
> Kaynaklar: [[2026-07-19 Proje Kurulum Brief]] + üç oturum import'u (16 Haziran – 20 Temmuz dönemini kapsar) + kod reposu `PROJECT_STATUS.md`.

## Güncel Ürün Durumu
- Çalışan **iOS prototipi** var (LiDAR'lı iPhone): oda tarama (RoomPlan) → 4-8 köşe fotoğrafı → materyal analizi → texture'lı 3D oda → AI Designer wizard (tarz/bütçe) → .usdz mobilyalı tasarım sahnesi → Blender render galerisi (4 açı) + USDZ.
- **İlk ürün kapsamı kararlaştı (2026-07-21)**: tarama→görselleştirme deneyimi + ince lead katmanı; **checkout ilk sürümde yok, ileride gelecek** → [[2026-07-21 İlk ürün kapsamı görselleştirme + lead]].
- **Hedef kullanıcı anı kararlaştı (2026-07-21)**: taşınma + tadilat/yenileme; tek parça alım ileriki sürüme ertelendi → [[2026-07-21 Hedef kullanıcı anı — taşınma ve tadilat]].
- Hâlâ açık: edinme kanalı, gelir modeli detayı, LiDAR stratejisi — bkz. [[Open Questions]].
- Katalog: yalnızca 3 usdz'li test ürünü (gerçek katalog doldurulmadı — öncelikli iş; satıcı adayı var, görüşülmedi).

## Güncel Teknik Durum
- Yığın: SwiftUI iOS + NestJS/Prisma/Supabase + Cloudflare R2 + Modal (Blender, T4) + OpenAI GPT-4o + Replicate flux-schnell + Tripo3D. Detay: [[System Architecture]].
- **Aktif 3D yolu**: RoomPlan geometri + fotoğraftan birebir kırpılan texture + Modal'da headless Blender render/USDZ. Detay: [[3D Render Pipeline]].
- Backend dev ortamında kurucu Mac'inde koşuyor (mDNS); **production deployment tamamen açık** — [[Deployment Strategy]].

## Oda Tarama Durumu
- Temel: Apple RoomPlan (güvenilir). Yaklaşım geçmişi ve sonuçları: [[Room Scanning Approaches]] (gsplat başarısız→rafta; ARKit mesh çalıştı→offline; RoomPlan+AI texture aktif).
- Son eklenen: tarama akışına isteğe bağlı zemin/duvar yakın çekim adımları (push edildi; cihaz doğrulaması bekliyor).

## Çalıştığı Bilinenler
- RoomPlan tarama + saf Transform render; Kat Planı/Roomplan/Render sekmeleri; AI Designer wizard (4 adım; pgvector + GPT-4o iç mimar rolü + yerleşim doğrulama); Blender pipeline (test odası + gerçek oda render'ları); fotoğraftan texture kırpma + mirror tile; Tripo3D ürün 3D kuyruğu; brand-panel satıcı ürün yükleme (Haziran'da uçtan uca doğrulandı; güncel durumu Needs Validation); LivaroTheme tasarım sistemi; mDNS bağlantı; presigned R2 akışı.

## Başarısız / Rafta Olduğu Bilinenler
- Gaussian Splatting (ARKit pozları yetersiz — kanıtlı; rafta, kod duruyor).
- ARKit Scene Reconstruction mesh+texture (çalıştı; ısınma/crash → bayrakla kapalı).
- Generatif fotogerçekçi render (gpt-image-1/ControlNet — geometri sadakati yok; superseded).
- Detay: [[Experiment Index]].

## Güncel Öncelikler (Now)
1. Yakın çekim texture akışının cihazda uçtan uca doğrulaması.
2. Blender pipeline gerçek-veri testleri (floorPolygon, Tripo ölçek/rotasyon, USDZ/QuickLook, boolean kesimler).
3. Katalog doldurma (Tripo3D'den gerçek ürünler).
4. Ürün kararlarının netleşmesi (MVP, ilk kullanıcı, ticari model) — bkz. [[Open Questions]].

## Güncel Blocker'lar
- Bilinen aktif blocker yok. (Geçmişte: Modal kredi tükenmesi — çözüldü; Replicate kredisi — yüklendi.)

## Son Kararlar
- [[2026-07-21 Hedef kullanıcı anı — taşınma ve tadilat]]
- [[2026-07-21 İlk ürün kapsamı görselleştirme + lead]]
- [[2026-07-19 Tarama akışına zemin-duvar yakın çekim adımları]]
- [[2026-07-18 Texture fotoğraftan birebir kırpılır]]
- [[2026-07-16 Render Modal üzerinde headless Blender]]
- Tam liste: [[Decision Index]].

## Bilinen Riskler / Dikkat
- Texture pipeline regresyona açık (iki kez yaşandı) — değişikliklerde log/R2 doğrulaması: [[Known Pitfalls]].
- RoomPlan'ın TV'yi pencere sanması gibi veri hataları çıktıya yansıyor.
- LiDAR'lı iPhone zorunluluğu pazarı daraltıyor (ele alınmadı).
