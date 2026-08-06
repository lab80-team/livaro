---
type: decision
status: accepted
created: 2026-08-06
source: "[[2026 08 06 Thinking Session — Uygulama User Journey]]"
related: []
---

# "Yeniden tasarla" hakkı yalnız kullanıcı isteğinde yanar

## Bağlam
[[2026-07-24 MVP tasarım kapsamı — oda boşaltılır, sıfırdan tasarım]] kararında "yeniden tasarla 2 hak" vardı ama **kuralı yazılmamıştı** ve bugün kodda sayaç hiç yok — "Yeniden Tasarla" sadece sihirbazı tekrar açan bir düğme. Kural sıfırdan yazılacağı için doğrusunu ilk seferde yazmanın ek maliyeti yok.

## Karar
Üç ayrı durum, üç ayrı davranış:

| Durum | Kullanıcıya gösterilen | Hak yanar mı |
|---|---|---|
| **Sistem hatası** (zaman aşımı, çökme, sunucu) | "Bizim tarafımızdaki bir aksaklık — yeniden tasarlama hakkınızdan düşmedi." + "Tekrar dene" (aynı cevaplarla, sorular yeniden sorulmadan) | **Hayır** |
| **Uygun ürün bulunamadı** (katalog dar, bütçe düşük) | Hata değil, sonuç: "Bu bütçe ve tarza uyan yeterli ürün bulamadık." + "Bütçeyi değiştir" / "Tarzı değiştir" | **Hayır** |
| **Kullanıcı beğenmedi → "Yeniden Tasarla"** | Onay penceresi: "2 yeniden tasarlama hakkınızdan biri kullanılacak." | **Evet** |

Ek metinler:
- Son hakta: "Bu son yeniden tasarlama hakkınız."
- Hak bittiğinde: "Bu oda için yeniden tasarlama hakkınız kalmadı. Odayı yeniden tarayarak yeni bir tasarım başlatabilirsiniz."

**Kısmi başarı** (tasarım çıktı, fotogerçekçi görüntü çıkmadı): tasarımın tamamı çöpe atılmaz. Kat planı + ürünler gösterilir, üstte tek satır uyarı + "Görüntüyü tekrar dene". Bu hâlde de hak yanmaz.

## Gerekçe
[[2026-08-05 Sistem hatasında 3D deneme hakkı iade edilir]] kararının aynı ilkesi: bizim hatamız yüzünden kullanıcı hakkını kaybetmemeli. Aynı problem için iki ayrı kural yazmak gereksiz.

## Değerlendirilen Alternatifler
- Her tasarım üretiminde yansın (maliyet freni en sıkı çalışır, ama kullanıcıya haksızlık).
- Sayaç MVP'ye hiç girmesin (her tasarım gerçek para yakıyor; birim maliyet hiç ölçülmedi).

## Sonuçlar (Consequences)
- Hak sayacı sıfırdan yazılacak (görev: [[Task Board]]).
- Toplam yeni tasarım sayısında kısa vadede sınır yok (24 Temmuz kararı geçerli); sınırlanan yalnız **aynı oda için yeniden tasarlama**.

## Riskler
- "Sistem hatası" ile "kullanıcı isteği" ayrımı yanlış kodlanırsa hak sessizce yanabilir; ayrım açık şekilde loglanmalı.

## İlgili Görevler
→ [[Task Board]]

## İlgili Bilgi
[[30 Knowledge/Product/Product Flows|Product Flows (Knowledge)]]

## Kaynak Toplantı
[[2026 08 06 Thinking Session — Uygulama User Journey]]
