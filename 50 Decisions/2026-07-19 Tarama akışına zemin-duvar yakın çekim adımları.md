---
type: decision
status: accepted
created: 2026-07-19
source: "[[2026-07-20 Oturum Import — Texture Pipeline ve Yakın Çekim]]"
related: []
---

# Tarama akışına zemin + duvar yakın çekim adımları eklenir (isteğe bağlı)

## Bağlam
Texture artık fotoğraftan birebir kırpılıyor ([[2026-07-18 Texture fotoğraftan birebir kırpılır]]) ama köşe fotoğraflarında temiz yüzey bölgesi bulmak GPT bbox seçimine bağlı ve mobilyalı odalarda riskli.

## Karar
Kurucu (18-19.07, plan onaylandı): Fotoğraf akışına iki **isteğe bağlı** adım eklenir:
Oda tara → 4 köşe foto → **zemin yakın çekim** (~30-50 cm, atlanabilir) → **duvar yakın çekim** (atlanabilir) → devam.
Yakın çekim varsa fotoğrafın tamamı zaten temiz yüzey → GPT bölge seçimine gerek kalmadan sabit merkez bölge kırpılarak doğrudan texture kaynağı olur.

## Gerekçe
GPT bbox bağımlılığını kaldırmak; texture kalitesini deterministik hale getirmek.

## Sonuçlar (Consequences)
- Fallback sırası: yakın çekim → köşe fotoğrafından GPT bölge kırpma → Replicate flux.
- Yakın çekimler R2'ye `src_floor.jpg` / `src_wall.jpg` olarak saklanır (yeniden üretimde de kullanılır).
- Değişen dosyalar (onaylı plan): `RoomPhotoCaptureView.swift` (faz makinesi: corners/floorCloseup/wallCloseup + tam ekran önizleme + adım göstergesi), `RoomCaptureFlowView.swift`, `generate-textures.dto.ts`, `room-scan.service.ts`. Dokunulmayacaklar: 4 köşe akışı, `analyze-materials`, `room_to_blender.py`, RoomPlan tarama, `RoomScene3DView.swift`.
- Uygulama durumu: plan onaylı; 19-20 Tem'de değişiklikler push edildi — cihazda uçtan uca doğrulama **Needs Validation**. Bkz. [[Task Board]].

## İlgili Bilgi
[[3D Render Pipeline]], [[Room Scanning Overview]]

## Kaynak
[[2026-07-20 Oturum Import — Texture Pipeline ve Yakın Çekim]] (18-19.07 mesajları; onaylı plan dosyası)
