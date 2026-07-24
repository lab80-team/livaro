---
type: knowledge
status: living
updated: 2026-07-24
aliases: ["Product Flows (Knowledge)"]
related: []
---

# Product Flows (Knowledge)

> Bu not, akışlar hakkında **bilinenleri** tutar. Akışların **tasarım durumu** (Not explored → Validated) için bkz. [[60 Planning/Product Flows|Product Flows (Planning)]].

## Şu An Bilinenler
- Tasarlanması gereken akışların bir listesi var (bkz. planlama notu).
- Prototipte çalışan akışlar var (tarama, AI tasarım, render — durumlar planlama notundaki tabloda "Prototype") ama hiçbir akış dış kullanıcıyla **Validated** değil.
- Tarama akışının güncel adımları: oda tara → 4-8 köşe foto → (isteğe bağlı, yeni) zemin + duvar yakın çekim → kayıt/analiz. Bkz. [[Room Scanning Overview]].
- **AI Designer wizard** (25 Haz'dan beri): 4 adım — (1) serbest metin ("Hayalinizdeki mekanı anlatın…"), (2) tarz seçimi (6 kart: Modern Lüks, Skandinav, Minimalist, Japandi, Klasik Şık, Boho), (3) renk paleti, (4) bütçe min/max ₺ → "AI ile Tasarla ✨". Sonuç: designConcept metni + 3D sahne (gerçek .usdz'lerle) + ürün kartları (designReason'lı) + "AR ile Odanda Gör" (otomatik yerleşim — kullanıcı elle yerleştirmez) + "Yeniden Tasarla". Tasarımlar `DesignResult` olarak kaydedilir; Projelerim'den geri dönülebilir.
- Ana navigasyon: 5 sekme (Ana Sayfa, Keşfet, Favoriler, Sepet, Profil); tarama Ana Sayfa'daki "Odayı Tara" CTA'sından. Bkz. [[2026-06-24 iOS tasarım sistemi LivaroTheme]].
- **Thinking session teyit ve eklemeleri (2026-07-24)**:
  - Wizard akışı **korunuyor** (serbest metin → tarz → renk → bütçe); anlatımdaki "önce bütçe, en son chat" sırası benimsenmedi. **Tarz kartlarına fotoğraf eklenecek**; karşılıklı konuşan **chat ileriki sürümde**.
  - Onay adımı: kullanıcı istediklerini anlattıktan sonra AI **özet sunar ve onay ister**; onay sonrası tasarım üretilir.
  - Tasarım sonucu otomatik çıkar (kullanıcı ayrıca render butonuna basmaz); yanında gerçekçi **2D fotoğraflar**.
  - MVP: dolu oda taranır, AI boşaltır, sıfırdan tasarlar; ürün çıkarma (yeri boş kalır); **AR tüm oda, MVP'de**; **yeniden tasarla 2 hak** (ilk belirleme) → [[2026-07-24 MVP tasarım kapsamı — oda boşaltılır, sıfırdan tasarım]].
  - **Çelişki (teyit bekliyor)**: ürünü alternatifle değiştirme MVP'de mi (cevap 9 "değiştirebilir" ↔ anlatım "MVP'de olmasın") → [[Open Questions]].
  - Welcome page vizyonu: güzel ev tasarımı arka planı + "Odayı tara" / "Projelerim" seçenekleri (tasarlanmadı).
  - Kurucuların açık sorusu: tek ürün değişiminde render'ın yeniden mi üretileceği, "anlık + gerçekçi"nin nasıl birlikte sağlanacağı. Claude/PM önerisi (karar değil): canlı 3D sahnede anlık değişiklik, fotogerçekçi render arka planda bildirimle → [[Open Questions]].
  - Kaynak: [[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu]].

## Varsayımlar
- Bazı akışlar basit, bazıları (özellikle oda tarama ve mobilya yerleştirme) gelişmiş olacak — **Needs Validation**.

## Bilinmeyenler
- Her akışın nihai adımları — **To Be Decided**.

## Önemli Sorular
- Hangi akışlar MVP'de zorunlu?

## İlgili Notlar
- [[60 Planning/Product Flows|Product Flows (Planning)]]
- [[User Onboarding]]
- [[Room Scanning Overview]]

## Kaynaklar
- [[Meeting Index]]
