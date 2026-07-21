---
type: decision
status: accepted
created: 2026-07-18
source: "[[2026-07-20 Oturum Import — Texture Pipeline ve Yakın Çekim]]"
related: []
---

# Zemin/duvar texture'ı fotoğraftan birebir kırpılır (generic üretim yalnızca fallback)

## Bağlam
İlk texture akışı: GPT-4o fotoğrafları analiz eder ("gri halı") → Replicate flux-schnell sıfırdan seamless texture üretir. Gerçek oda testinde sonuç gerçek odayla alakasız çıktı (gri halı yerine düz kahverengi zemin).

## Karar
Kurucu (18.07): "Texture üretimi gerçek odaya benzemiyor — **fotoğraftan birebir türetilmeli**." Kullanıcının köşe fotoğraflarından zemin/duvar bölgesi kırpılır (GPT-4o Vision'dan temiz bölge bounding box'ı istenir), kırpılan parça 2x2 **aynalı karo** (mirror tile) ile seamless'a yaklaştırılır ve doğrudan texture olarak kullanılır. Replicate generic üretim yalnızca son fallback'tir.

## Gerekçe
Kullanıcı kendi odasını tanımalı; "benzer" generic texture yerine gerçek materyalin kendisi.

## Sonuçlar (Consequences)
- Fallback sırası: (yakın çekim fotoğraf →) köşe fotoğrafından GPT bölge kırpma → Replicate flux üretimi.
- GPT bbox seçimi mobilyalı odalarda riskli → yakın çekim adımları planlandı: [[2026-07-19 Tarama akışına zemin-duvar yakın çekim adımları]].
- Regresyon dersi: kapı fix'i sırasında texture pipeline bozuldu ("zemin yine kahverengi") — texture yolu hassas, değişikliklerde log/R2 içeriğiyle doğrulama şart. Bkz. [[Known Pitfalls]].

## İlgili Bilgi
[[3D Render Pipeline]], [[Texture üretimi generic flux vs fotoğraftan kırpma]]

## Kaynak
[[2026-07-20 Oturum Import — Texture Pipeline ve Yakın Çekim]] (18.07 mesajları)
