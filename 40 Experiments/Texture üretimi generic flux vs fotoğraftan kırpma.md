---
type: experiment
status: active
owner: "[[Selim]]"
created: 2026-07-18
related: []
---

# Texture üretimi: generic flux vs fotoğraftan kırpma

## Soru
Render'daki zemin/duvar, kullanıcının **gerçek odasına** nasıl benzetilir?

## Hipotez (ilk): analiz + generic üretim yeter → YANLIŞLANDI
GPT-4o "gri halı" der → flux-schnell seamless "gri halı" üretir → yeterince benzer olur sanılıyordu. Gerçek oda testi (18 Tem): sonuç odayla alakasız (düz kahverengi zemin).

## Hipotez (revize): fotoğraftan birebir kırpma
Köşe fotoğrafından temiz zemin/duvar bölgesi kırpılır (GPT-4o bbox) → 2x2 aynalı karo (mirror tile) → doğrudan texture. Mükemmel seamless olmasa da "kendi odam" hissi verir.

## Kurulum
`room-scan.service.ts` (`cropMirrorTile`, öncelik zinciri), R2 `room-textures/{scanId}/`. Fallback sırası: yakın çekim → GPT bölge kırpma → flux generic.

## Sonuç (devam ediyor)
- Fotoğraftan kırpma çalıştı: "zemin gri tanecikli halı olarak doğru çıkıyordu" (18 Tem).
- İki kez **regresyon**: ilgisiz değişiklikler (kapı fix, textureSource) sonrası zemin yeniden kahverengi; git diff ile bulunup geri alındı.
- GPT bbox mobilyalı odalarda riskli → yakın çekim adımları planlandı ve onaylandı ([[2026-07-19 Tarama akışına zemin-duvar yakın çekim adımları]]); yakın çekim varsa sabit merkez bölge kırpılır, GPT'ye gerek kalmaz.
- Cihazda uçtan uca doğrulama (yakın çekimli akış) — **Needs Validation**.

## İşe Yarayan
Fotoğraftan kırpma + mirror tile; kaynak fotoğrafların R2'de saklanması (yeniden üretim).

## Başarısız Olan
Generic flux üretimi (gerçek odaya benzemiyor) — artık yalnızca son fallback.

## Karar / Sonuç
[[2026-07-18 Texture fotoğraftan birebir kırpılır]]

## İlgili Kod / Branch
`src/room-scan/room-scan.service.ts`, `src/room-scan/replicate.service.ts`, `ios/Livaro/Rooms/RoomPhotoCaptureView.swift`

## İlgili Kaynak
[[2026-07-20 Oturum Import — Texture Pipeline ve Yakın Çekim]]
