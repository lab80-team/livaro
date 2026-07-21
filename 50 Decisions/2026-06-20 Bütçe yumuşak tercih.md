---
type: decision
status: accepted
created: 2026-06-20
source: "[[2026-07-08 Oturum Import — Web Temelleri ve iOS Başlangıcı]]"
related: []
---

# AI aramada bütçe yumuşak tercih, oda ölçüsü sert filtre

## Bağlam
Faz 4 AI tasarımcı motoru (GPT-4o Türkçe parse + pgvector arama) tasarlanırken bütçenin nasıl uygulanacağı soruldu; ajanın önerisi sert filtreydi.

## Karar
Kurucu (AskUserQuestion yanıtı, ajan önerisinin tersine): **bütçe sert filtre değil, yumuşak tercih** — skor ağırlığı olarak uygulanır (BUDGET_WEIGHT=0.3; SIMILARITY_WEIGHT=0.7). **Oda ölçüsü ise sert filtredir** (sığmayan ürün önerilmez; ROOM_FIT_RATIO=0.6).

## Gerekçe
Bütçeyi biraz aşan ama çok uygun ürünü tamamen gizlemek kötü deneyim; odaya fiziksel olarak sığmayan ürünü göstermek ise her durumda yanlış.

## Sonuçlar (Consequences)
- `POST /ai/designer/search` skorlaması raw SQL'de (pgvector cosine + budget_fit); sıfır sonuç hata değil geçerli durum.
- Kullanıcıya dönük mesajlar Türkçe.

## İlgili Bilgi
[[System Architecture]] (AI Designer), [[Product Overview]]

## Kaynak
[[2026-07-08 Oturum Import — Web Temelleri ve iOS Başlangıcı]] (19-22 Haz Faz 4 tasarımı)
