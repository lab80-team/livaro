---
type: decision
status: accepted
created: 2026-07-24
source: "[[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu]]"
related: ["[[2026-07-24 PM Gözden Geçirme — Thinking Session]]", "[[Deployment Strategy]]"]
---

# PM önerileri kararları — bulut taşınma, kalite çıtası, bütçe rozeti

## Bağlam
PM 2. tur incelemesi ([[2026-07-24 PM Gözden Geçirme — Thinking Session]]) nihai karar setine "emniyet kemeri" önerileri sundu; kurucular tek tek cevapladı (Bölüm 4).

## Kararlar
- **KABUL — Backend buluta taşınacak** (öne çekildi): arka planda render + bildirim ve kullanıcı çekme hedefi her an açık sunucu gerektiriyor; backend kurucu Mac'inden buluta taşınacak.
- **KABUL — Dolu oda boşaltma + AR için iç kalite çıtası/kontrol noktası**: çıta tutmazsa lansmanı bloklamak yerine özellik "deneysel" etiketiyle sınırlı açılır (önce boş oda akışı sağlamlaştırılır).
- **KABUL — Bütçe aşımı rozeti**: bütçeyi aşan ürünler kullanıcıya "bütçenin %X üstünde" rozetiyle gösterilecek → [[2026-07-24 Bütçe aşım tavanı yüzde 10]].
- **RET — Maliyet freni (harcama tavanı/limit anahtarı) şimdilik gerek yok**: birim maliyet analizini kurucular kendileri yapacak, sonuçları sonra paylaşacaklar.
- **GPT-4o test detayları belirsiz**: gün sayısı, tarama sayısı, prompt kullanımı — hepsi **To Be Decided**; test MVP altyapısı bitince.

## Sonuçlar (Consequences)
- Buluta taşınma somut iş olarak [[Task Board]]'a eklendi; [[Deployment Strategy]] ve [[Roadmap]] güncellenmeli/güncellendi.
- PM'in kabul edilmeyen/cevaplanmayan önerileri (tek sayfalık iade akışı + hizmet bedeli kural seti, render sürüm/etiket kuralı, bot koruması) öneri statüsünde → [[Open Questions]].

## Kaynak Toplantı
[[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu]] (Bölüm 4)
