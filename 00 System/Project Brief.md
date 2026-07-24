---
type: system
status: living
updated: 2026-07-20
---

# Project Brief

> Bu not, doğrulandıkça güncellenir. Bilinmeyen alanlar `Unknown` / `To Be Decided` / `Needs Validation` olarak işaretlenir. Uydurma bilgi eklenmez.

## Özet
Online bir mobilya pazaryeri girişimi. Çalışan vizyon: **LiDAR oda tarama → AI iç mimarlık tasarımı → gerçek ölçülü 3D görselleştirme → ürün satışı** (kaynak: kod reposu `PROJECT_STATUS.md`). İki kurucu: [[Selim]], [[Yusuf]].

## Keşfedilen Problem
- **Kurucu hipotezi netleşti (2026-07-24)**: mobilya/ev düzenleme alışverişi 1-2 ay mağaza gezmek demek; ürünler odada bir arada görülemiyor, bütçe tek yerde takip edilemiyor, profesyonel tasarım desteği yok → zaman + enerji kaybı. Dış doğrulama yok (**Needs Validation**). Bkz. [[User Problems]].

## Olası Hedef Kullanıcılar
- **Kararlaştı (2026-07-21, netleştirildi 2026-07-24)**: taşınma + tadilat/yenileme anındaki kullanıcılar; MVP'de oda sıfırdan tasarlanır. İlk pazar Türkiye; MVP alıcıları LiDAR'lı iPhone sahipleri. Bkz. [[Target Users]].

## Olası Pazaryeri Katılımcıları
- Alıcılar (müşteriler) — **Needs Validation**
- Satıcılar (mobilya satıcıları / mağazalar) — **Needs Validation**
- Diğer katılımcılar (ör. montaj, lojistik) — **Unknown**
- Bkz. [[Marketplace Model]]

## Prototype Durumu (20 Tem itibarıyla)
- Çalışan iOS prototipi + backend var; uçtan uca akış: tarama → fotoğraflar → texture'lı 3D oda → AI tasarım → render. Detay: [[Current State]], [[System Architecture]].
- Oda tarama denemelerinin somut sonuçları deney notlarında: [[Experiment Index]] (gsplat başarısız/rafta, ARKit mesh offline, RoomPlan+AI texture aktif).
- Kaynaklar: [[2026-07-19 Proje Kurulum Brief]] + oturum import'ları (Inbox, 7-20 Tem).

## Bilinen Ekip Üyeleri
- [[Selim]] (kurucu; okul +2 yıl), [[Yusuf]] (kurucu; okul +6 ay), [[Ali Abi]] (AI danışmanı)
- Finansman planı (2026-07-24, kurucu beyanı): ilk yatırım babalardan (meblağ **Unknown**); büyüdükçe melek yatırımcı hedefi; yatırım aldıkça ekip kurulacak.

## Güncel Belirsizlikler
- ~~İlk ürünün (MVP) kapsamı~~ — büyük ölçüde **kararlaştı** (21+24 Tem kararları → [[Decision Index]]); bekleyen teyitler: [[Open Questions]]
- ~~Ticari model~~ — **kararlaştı**: sepet MVP'de, checkout ödeme teknolojisi seçilince; gelir kısa vadede %10 komisyon → [[Marketplace Model]]
- ~~LiDAR'sız cihaz stratejisi~~ — **kararlaştı**: MVP LiDAR-only; LiDAR'sız çözüm ileride → [[2026-07-24 MVP yalnızca LiDAR'lı iPhone]]
- İlk kullanıcılar / edinme kanalı — **To Be Decided** (ilk test kurucu çevresinde)
- Kayıt/onboarding akışı — **To Be Decided** (misafir gezinme serbest teyit edildi; welcome page tasarlanmadı)
- Ödeme sağlayıcısı + emanet/lisans sorusu — **To Be Decided**
- Production deployment — **To Be Decided**
- Bkz. [[Open Questions]]

## Başlangıç Ürün Hedefleri
- **To Be Decided** — Ekip henüz netleştirmedi.

## Teknik Hedefler (fiilî, oturumlardan)
- Gerçek ölçülere sadık, kullanıcının "kendi odam" diyeceği 3D çıktı; cihazda hızlı tarama; maliyeti düşük render altyapısı. Resmî hedef listesi **To Be Decided**.

## İş Hedefleri
- **To Be Decided** — Bkz. [[Marketplace Model]].
