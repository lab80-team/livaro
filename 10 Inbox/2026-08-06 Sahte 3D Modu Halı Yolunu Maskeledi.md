---
type: import
source: claude-session
date: 2026-08-06
---

# 2026-08-06 Sahte 3D Modu Halı Yolunu Maskeledi (kod reposu)

Kaynak: 6 Ağustos Claude oturumu. Kurucu mağaza panelinde bir halı yükledi; "3D modeliniz hazır" denince çıkan model halıyla tamamen alakasızdı. Teşhis → düzeltme → Codex incelemesi → main merge aynı oturumda yapıldı.

## Kurucunun bildirdiği kusur

Yüklenen fotoğraf: uzun ince Hereke tipi halı (tepeden, düz zeminde). Panelde 3D olarak görünen: yuvarlak köşeli, kalın, dokusuz bir kutu — üstü açık gri, gövdesi koyu. Halıyla hiçbir benzerliği yok.

## Teşhis (ölçülerek, tahminle değil)

Üretim hiç yapılmamıştı. Panelde görünen model, **16 Haziran'dan kalma "Pipeline Test Sofa"** adlı test kanepesiydi (200 × 90 × 85 cm).

Kanıt zinciri:
1. Yerel `.env`'de `TRIPO3D_FAKE=1` açık kalmıştı; bu bayrak açıkken boru hattı hiç üretim yapmaz, `TRIPO3D_FAKE_GLB_URL`'deki sabit dosyayı yazar.
2. Veritabanında "Sultani" halısının `glbUrl` alanı, `.env`'deki sabit demo adresiyle **birebir aynı** çıktı.
3. Düz yüzey yolu çalışsaydı dolması gereken `modelWidthCm/HeightCm/DepthCm` alanları **boştu**.
4. Sabit adresteki ürün id'si sorgulandı → "Pipeline Test Sofa", 16 Haziran 2026.

## Kök neden

`three-d-pipeline.processor.ts` içinde sahte mod kontrolü **kategori seçiminden ÖNCE** çalışıyordu:

```
if (TRIPO3D_FAKE === '1') { sabit demo GLB'sini yaz; çık }   ← her kategori buraya düşüyordu
const strategy = categoryModelStrategy(...)                   ← buraya hiç gelinmiyordu
```

Oysa sahte modun tek amacı geliştirmede **Tripo kredisi yakmamak**. Düz yüzey (halı) yolu dış servise hiç uğramaz ve kredi harcamaz — orada sahteye düşmek, satıcıya başka bir ürünün modelini göstermekten başka işe yaramıyordu. Bkz. [[2026-07-29 Kategori bazlı 3D üretim stratejisi — halı düz yüzey, mobilya Tripo devam, perde sonraya]].

## Düzeltme

Koşul strateji seçiminden **sonraya** alındı ve yalnız Tripo yoluna bağlandı:

```
const strategy = categoryModelStrategy(...)
if (strategy === 'tripo' && TRIPO3D_FAKE === '1') { ... }
```

Yani halı, ayar ne olursa olsun her zaman gerçek üretilir; mobilyada geliştirme kredisi korunur.

3 regresyon testi eklendi: halıda sahteye düşmez, mobilyada düşer, kategorisi bilinmeyen eski kayıtta (Tripo fallback) düşer. Testler önce kırmızıydı, düzeltmeyle yeşile döndü.

## Doğrulama

- **607 backend testi yeşil**; yeni tip hatası yok (değişiklik öncesi/sonrası hata sayısı ölçüldü: 19 = 19, hepsi mevcut spec dosyalarından).
- **Gerçek fotoğrafla kanıt**: "Sultani"nin kendi fotoğrafından `npm run flat:glb` ile üretilen model **207 × 300,5 cm × 6 mm** ince dilim çıktı, dokusu gerçek halı fotoğrafı (arka plan kırpıldı, saçak kenarı saydam). Sahte modelle karşılaştırma: 200 × 90 × 85 cm kanepe kutusu.
- Codex inceleme turu: **bulgu yok**.
- `.env`'de `TRIPO3D_FAKE=0` yapıldı (kurucu kararı). Not: bu ayar kapalıyken **mobilya** yüklenirse gerçek Tripo çalışır ve kredi yanar; halı etkilenmez.

## Yan bulgular (bu turda düzeltilmedi)

1. **Sistem hatasıyla bozulmuş bir modeli kurtarmanın yolu yok.** "Sultani" AWAITING_ADMIN durumundaydı; admin `retry3D` yalnız STUCK ürünleri kabul ediyor, satıcı `submitTo3D` ise `lastImageSetHash` ile "aynı fotoğraflarla tekrar üretim yapılamaz" diyor. Fotoğraf sorunlu değildi, sistem sorunluydu. Ürünü kurtarmak için veritabanına elle müdahale gerekti (durum → DRAFT, foto kilidi açıldı, yanan 1 hak iade edildi — kurucu onayıyla, yalnız bu ürün). Bu, [[2026-08-05 Sistem hatasında 3D deneme hakkı iade edilir]] kararının kapsamadığı bir boşluk → [[Open Questions]].
2. **`flat:glb` script'inin ölçü doğrulaması saçak payını yok sayıyor**: üretim doğru olduğu halde sonunda "✗ Ölçü doğrulaması BAŞARISIZ: boy 300.502 ≠ 300" yazıyor. Saçak, 5 Ağustos kararıyla nominal ölçünün dışında modelleniyor ([[2026-08-05 Halı ölçüsü saçak hariç — saçak ayrı yassı şerit olarak modellenir]]) ama script hâlâ birebir eşitlik bekliyor. Yalnızca elle deneme aracı, üretimi etkilemiyor.

## İlgili Notlar

[[Known Pitfalls]], [[3D Render Pipeline]], [[Seller Experience]], [[Current State]], [[2026-08-06 Halı Doku Delikleri, Saçak Modeli ve Migration Kurtarması]]
