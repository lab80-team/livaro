---
type: decision
status: accepted
created: 2026-07-24
source: "[[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu]]"
related: ["[[3D Render Pipeline]]", "[[30 Knowledge/Product/Product Flows|Product Flows (Knowledge)]]"]
---

# Anlık deneyim — canlı 3D sahne, render arka planda

> ⚠️ **GÜNCELLENDİ (2026-08-06)**: İlke aynı (anında bir şey göster, fotogerçekçi görüntüyü arkada üret) ama iki şey değişti — gösterilen model artık **Blender sahnesinden** geliyor ve fotogerçekçi fotoğraf **ayrı bir yerde değil, aynı ekranda** şeritle sunuluyor. Bildirim MVP'den çıktı (altyapı hiç yok) → [[2026-08-06 Tasarım sonuç ekranı — döner Blender modeli, fotogerçekçi render arkada]], [[2026-08-06 Tasarım beklemesi arka planda sürer — üst şerit haber verir]].

## Bağlam
Kurucuların sorusu: "hem anlık hem gerçekçi görüntüyü nasıl sağlarız; tek mobilya değişince komple yeniden mi render olur?" Fotogerçekçi Blender render'ı 2-3 dk sürüyor. Claude ve PM incelemesi aynı öneriye vardı; kurucu teyit turunda onayladı ("telefondaki 3D sahneyi onaylıyorum").

## Karar
- **Canlı 3D sahne (cihazda, RealityKit) ana etkileşim katmanıdır**: ürün ekleme/çıkarma/değiştirme orada **anında** görünür.
- **Fotogerçekçi render arka planda üretilir**, hazır olunca bildirimle gelir.
- **Tek ürün değişimi tam render tetiklemez**; render, tasarım netleşince/istenince çalışır.

## Gerekçe
Kullanıcı 2-3 dk boş ekran beklememeli; mevcut mimari (cihazda canlı sahne + sunucuda Blender) bu ayrıma zaten uygun.

## Sonuçlar (Consequences)
- Sonuç ekranı tasarımı canlı 3D sahne merkezli kurgulanır; "gerçekçi fotoğraf" ayrı bir çıktı olarak sunulur.
- Render kuyruğu/bildirim akışı tasarlanmalı (hata UX'i hâlâ açık → [[Open Questions]]).

## Kaynak Toplantı
[[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu]] (Bölüm 3, teyit turu)
