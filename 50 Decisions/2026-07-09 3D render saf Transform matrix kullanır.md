---
type: decision
status: accepted
created: 2026-07-09
source: "[[2026-07-16 Oturum Import — 3D Pipeline Evrimi]]"
related: []
---

# 3D render saf Transform(matrix:) kullanır — manuel rotasyon yasak

## Bağlam
RoomPlan taramasından gelen kapı/pencere/mobilyalar 3D sahnede defalarca çapraz/dağınık çıktı. Her "düzeltme" (2D segment uçlarından atan2 ile rotasyon türetme, `nearestWallMatch`, `makeSegmentBox` fallback'leri) modeli tekrar bozdu.

## Karar
RoomPlan elemanları (duvar/kapı/pencere/obje) **yalnızca** `entity.transform = Transform(matrix:)` + `MeshResource.generateBox(size: dimensions)` ile render edilir. Manuel rotasyon türetme, atan2, segment rekonstrüksiyonu **yasak**. (Tek kabul edilen atan2 kullanımı: ölçü etiketlerini kameraya döndürme/billboarding.)

## Gerekçe
RoomPlan transform'u zaten doğru rotasyonu içeriyor; ara temsile indirgeyip geri türetmek kayıplı ve her seferinde bozdu. Kurucu 09.07'de kesin kural koydu; 16.07'de yeni işlerde de "bu pattern kesinleşmiş, değiştirme" diye teyit etti.

## Değerlendirilen Alternatifler
- 2D segment + atan2 rekonstrüksiyonu — defalarca denendi, hep çapraz kapı/pencere üretti.

## Sonuçlar (Consequences)
- Referans commit: `ae2fd87` ("Faz 5: RoomPlan transform doğrudan kullanım").
- JSON'da transform'un 16 float'ı (column-major) + dimensions'ın 3 float'ı kayıpsız saklanmalı; render anında doğrudan kullanılır.
- Render bozuksa neden neredeyse her zaman **veri**dir: eski taramalarda `transform`/`dimensions` alanları yok → yeniden tarama gerekir. Önce DB kontrol edilir, render koduna dokunulmaz. Bkz. [[Known Pitfalls]].

## İlgili Bilgi
[[3D Render Pipeline]], [[System Architecture]]

## Kaynak
[[2026-07-16 Oturum Import — 3D Pipeline Evrimi]] (09.07 mesajları)
