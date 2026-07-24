---
type: system
status: living
updated: 2026-07-24
---

# Current State

> Projenin **şu anki** özeti. Sürekli güncellenir. **Tarihçe tutulmaz** — geçmiş, kaynak notlarda ([[Meeting Index]], Inbox import'ları) ve Git'te.
>
> Kaynaklar: [[2026-07-19 Proje Kurulum Brief]] + üç oturum import'u (16 Haziran – 20 Temmuz dönemini kapsar) + kod reposu `PROJECT_STATUS.md`.

## Güncel Ürün Durumu
- Çalışan **iOS prototipi** var (LiDAR'lı iPhone): oda tarama (RoomPlan) → 4-8 köşe fotoğrafı → materyal analizi → texture'lı 3D oda → AI Designer wizard (tarz/bütçe) → .usdz mobilyalı tasarım sahnesi → Blender render galerisi (4 açı) + USDZ.
- **Uçtan uca vizyon kayda geçti (2026-07-24 thinking session)**: gerçek ürünlerle AI oda tasarımı + pazaryeri + operasyon aracılığı; problem hipotezi netleşti → [[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu]], [[User Problems]].
- **MVP kapsamı (21 Tem + 24 Tem kararları)**: sıfırdan tasarım (dolu oda AI ile boşaltılır), ürün çıkarma, AR (tüm oda), **sepet MVP'de — checkout ödeme teknolojisi seçilince**, yalnızca LiDAR'lı iPhone, bütçe aşım tavanı ~%10, yeniden tasarla 2 hak. Kararlar: [[Decision Index]].
- **Hedef kullanıcı anı (2026-07-21, teyit 24 Tem)**: taşınma + tadilat/yenileme; tek parça alım ileride → [[2026-07-21 Hedef kullanıcı anı — taşınma ve tadilat]].
- **Gelir planı (2026-07-24)**: kısa vade %10 komisyon, orta vade reklam (Sponsorlu etiketli), uzun vade indirim/hizmet bedeli; şimdilik kullanıcıya ücretsiz → [[Marketplace Model]].
- **Pilot marka kriterleri kararlaştı**: her kategoriden 2 internette satan firma; mağazalara MVP bitince gidilecek → [[2026-07-24 Pilot marka kriterleri]].
- Bekleyen teyitler (24 Tem oturumundan): alternatifle değiştirme MVP'de mi; checkout öncesi sepet davranışı; anlık/gerçekçi görüntü stratejisi → [[Open Questions]].
- Katalog: yalnızca 3 usdz'li test ürünü (gerçek katalog pilot markalardan dolacak; henüz hiçbir satıcıyla görüşülmedi).

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
4. **GPT-4o yerleşiminin kapsamlı testi** (sonuca göre teknoloji kararı — 24 Tem, cevap 14).
5. Kalan ürün belirsizliklerinin kapatılması (bekleyen teyitler, ödeme sağlayıcısı, birim maliyet) — bkz. [[Open Questions]].

## Güncel Blocker'lar
- Bilinen aktif blocker yok. (Geçmişte: Modal kredi tükenmesi — çözüldü; Replicate kredisi — yüklendi.)

## Son Kararlar
- [[2026-07-24 Sepet MVP'de, checkout ödeme teknolojisi seçilince]]
- [[2026-07-24 MVP yalnızca LiDAR'lı iPhone]]
- [[2026-07-24 MVP tasarım kapsamı — oda boşaltılır, sıfırdan tasarım]]
- [[2026-07-24 Bütçe aşım tavanı yüzde 10]]
- [[2026-07-24 Pilot marka kriterleri]]
- [[2026-07-21 Hedef kullanıcı anı — taşınma ve tadilat]]
- Tam liste: [[Decision Index]].

## Bilinen Riskler / Dikkat
- Texture pipeline regresyona açık (iki kez yaşandı) — değişikliklerde log/R2 doğrulaması: [[Known Pitfalls]].
- RoomPlan'ın TV'yi pencere sanması gibi veri hataları çıktıya yansıyor.
- LiDAR'lı iPhone zorunluluğu pazarı daraltıyor (bilinçli geçici kısıt — [[2026-07-24 MVP yalnızca LiDAR'lı iPhone]]).
- PM incelemesinin (24 Tem) öne çıkardığı riskler: emanet para = lisans sorunu; "iptal yok" ↔ 14 gün cayma hakkı; AI yerleşim kalitesi ölçülmedi; birim maliyet bilinmeden ücretsiz model; kapsam-kaynak uçurumu → [[2026-07-24 PM Gözden Geçirme — Thinking Session]].
