---
type: decision
status: accepted
created: 2026-08-06
source: "[[2026 08 06 Thinking Session — Uygulama User Journey]]"
related: []
---

# MVP LiDAR'sız telefonlara açılıyor — geçici olarak "haber ver" listesi

## Bağlam
[[2026-07-24 MVP yalnızca LiDAR'lı iPhone]] kararı MVP'yi LiDAR sensörlü iPhone Pro modelleriyle sınırlıyordu. Kurucu bu kısıtı kaldırdı: "lidarsız telefonlara da ulaşmamız gerekiyor, onların uygulamayı kullanabilmesi gerekiyor." Ancak LiDAR'sız cihazlarda odayı ölçecek teknoloji **hâlâ seçilmedi** (araştırılıyor). Bugün bu cihazlarda ekran "LiDAR Gerekli — Kapat" deyip kullanıcıyı çıkmaz sokağa sokuyor.

## Karar
1. **Hedef genişledi**: LiDAR'sız telefonlar artık ürün hedefinin dışında değil. Doğru teknoloji bulunduğunda eklenecek.
2. **MVP'nin fiili kapsamı yine LiDAR'lı iPhone** — teknoloji seçilmeden tarama açılamaz.
3. **Geçici deneyim**: LiDAR'sız cihazda "Odayı Tara"ya basan kullanıcı üç şey görecek — dürüst açıklama, **"Haber ver"** butonu (tek dokunuş, iletişim bilgisi zaten elimizde) ve **"Ürünlere göz at"** yönlendirmesi. Tarih verilmeyecek ("yakında" denebilir, "ağustos sonunda" denemez).

Önerilen metin:
> **Bu telefonda oda tarama henüz yok**
> Oda taraması şu an yalnızca LiDAR sensörlü iPhone modellerinde çalışıyor. Diğer telefonlar için bir yol üzerinde çalışıyoruz. Hazır olduğunda size haber verelim mi?
> [Haber ver] [Ürünlere göz at]

## Gerekçe
- Denenmiş üç yöntemin üçü de elendi: Gaussian Splatting (rafta), ARKit mesh (ısınma/çökme nedeniyle kapalı), üretken görüntü (ölçü sadakati yok). Yerine konacak kanıtlanmış bir yöntem yok.
- Ölçü, zincirin **tamamının** girdisi: Blender sahnesi, ürünün odaya sığma filtresi, AR — hepsi gerçek metre değerine bağlı. Doğrulanmamış bir ölçüm yöntemi ürünün tek somut vaadini ("gerçek ürünler, gerçek ölçüler") çürütür.
- "Haber ver" listesi bir ekran ve bir listeden ibaret; yan faydası büyük: **LiDAR'sız talebin bugün hiç bilmediğimiz gerçek sayısını** verir. Kararın kendisi bu belirsizliğin üstüne kurulu.

## Değerlendirilen Alternatifler
- **Elle ölçü girişi** (kullanıcı en/boy/yükseklik yazar): kapı, pencere ve odanın gerçek şekli kaybolur; tasarım kalitesi düşer. Reddedilmedi — pilot sonrası küçük bir deneme olarak masada.
- **MVP'yi teknoloji gelene kadar bekletmek**: çıkış tarihi tamamen belirsizleşir.
- **Ayrı Android uygulaması**: reddedildi — "Android ile giriş" ifadesi **Google hesabıyla giriş** anlamına geliyor; uygulama iPhone'da kalıyor.

## Sonuçlar (Consequences)
- Bugünkü "LiDAR Gerekli — Kapat" ekranı değişecek (görev: [[Task Board]]).
- Bekleme listesi için basit bir kayıt yeri gerekiyor.
- Pilot kullanıcılar hâlâ Pro model sahiplerinden seçilecek.

## Riskler
- Bekleme listesine yazılan kullanıcı uzun süre haber alamazsa güven kaybı olur.
- LiDAR'sız çözüm geldiğinde ölçü doğruluğu düşük çıkarsa iki sınıf deneyim doğar; kullanıcıya bunun söylenip söylenmeyeceği **açık** → [[Open Questions]].

## İlgili Görevler
→ [[Task Board]]

## İlgili Bilgi
[[Room Scanning Overview]], [[Room Scanning Approaches]], [[User Onboarding]]

## Kaynak Toplantı
[[2026 08 06 Thinking Session — Uygulama User Journey]]
