---
type: decision
status: accepted
created: 2026-08-06
source: "[[2026 08 06 Thinking Session — Uygulama User Journey]]"
related: []
---

# Render güzelleştirme katmanı kapatılır — saf Blender çıktısı

## Bağlam
Bugün Blender'ın ürettiği 4 görüntüden **yalnız birine** (göz hizası karesi) yapay zekâ ile "güzelleştirme" uygulanıyor (`_enhance_render`, Replicate flux img2img). Bu, [[2026-07-15 RoomPlan geometri + AI texture varsayılan 3D yaklaşımı]] turunda "geometri/ölçü sadakati yok" gerekçesiyle elenen üretken yöntemin arka kapıdan geri dönmüş hâli. Sonucu: 4 açı birbiriyle tutarsız görünüyor ve görüntü bir miktar değişiyor.

## Karar
**Güzelleştirme katmanı kapatılacak; kullanıcıya saf Blender çıktısı gösterilecek.**

## Gerekçe
- Satılan koltuk ile görüntüdeki koltuk birebir aynı kalmalı. Bir pazaryerinde en pahalı hata, gelen ürünün resimdekinden farklı çıkmasıdır.
- 4 açının biri güzelleştirilmiş, üçü değil — tutarsızlık zaten görünür durumda.
- Bu katmanın çıktıyı ne kadar değiştirdiği **hiç ölçülmedi**.

## Değerlendirilen Alternatifler
- **Bugünkü gibi kalsın**: tutarsızlık sürer.
- **Tüm açılarda çalışsın**: görünüm tutarlı ve daha etkileyici olur; sapma riski ve maliyet artar. Etkisi ölçülmeden açılmamalı — ileride ölçülüp yeniden değerlendirilebilir.

## Sonuçlar (Consequences)
- Fotogerçekçilik yükü tamamen Blender'ın omuzlarına biner; kalite beklenmedik şekilde düşerse Blender ayarları (ışık, örnekleme, malzeme) üzerinden çözülecek.
- Replicate flux kullanımı bu yolda düşer (maliyet azalır).

## Riskler
- Saf Blender çıktısı, kurucunun beklediği "çok gerçekçi" çıtayı karşılamayabilir; ilk gerçek odada gözle değerlendirilmeli.

## İlgili Görevler
→ [[Task Board]]

## İlgili Bilgi
[[3D Render Pipeline]], [[Experiment Index]]

## Kaynak Toplantı
[[2026 08 06 Thinking Session — Uygulama User Journey]]
