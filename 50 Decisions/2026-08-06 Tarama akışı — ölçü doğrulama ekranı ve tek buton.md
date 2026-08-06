---
type: decision
status: accepted
created: 2026-08-06
source: "[[2026 08 06 Thinking Session — Uygulama User Journey]]"
related: []
---

# Tarama akışı — ölçü doğrulama ekranı ve tek buton

## Bağlam
Kurucu: RoomPlan çıktısı yalnız taramadan sonra, ölçü/şekil doğrulaması için gösterilsin; **mobilyalar gösterilmesin**; altında bunun göstermelik olduğunu söyleyen bir not olsun; bir daha hiç gösterilmesin. Ayrı duran "Kaydet" ve "Odayı Tasarla" butonları tek butona insin.

## Karar
**Akışın son hâli**: oda tara → 4-8 köşe fotoğrafı + zemin/duvar yakın çekimi → **ölçü doğrulama ekranı** → "Kaydet ve Odayı Tasarla" → oda ismi → doğrudan 4 soru.

1. **Köşe fotoğrafı ve yakın çekim adımları kalıyor** ([[2026-07-19 Tarama akışına zemin-duvar yakın çekim adımları]] geçerli) — odanın gerçek dokusu (parke, boya) buradan çıkıyor; "benim odam" hissinin kaynağı bu.
2. **Ölçü doğrulama ekranı**: başlık "Ölçüler doğru mu?"; **mobilyasız** oda görünümü; tek satır ölçü özeti (Alan · Boyutlar · kapı/pencere sayısı); iki yol — **"Ölçüler doğru, devam et"** ve **"Yeniden tara"**.
3. **Bu ekranda "Kat Planı | 3D" seçici olmayacak** — tasarım ekranındaki seçiciyle karışmaması için.
4. Bu görünüm **bir daha gösterilmez**; tasarım ekranındaki "3D" sekmesi Blender modelini gösterir.
5. **Not metni** — "göstermelik" kelimesi kullanılmayacak (kulakta "sahte/göz boyama" diye tınlıyor ve tam güven kurulması gereken anda güveni zedeliyor):
   > Bu **taslak görünüm** yalnızca ölçüleri kontrol etmeniz için — odanızın gerçek görüntüsü değil. Tasarımınız bir sonraki adımda çok daha gerçekçi olacak.
6. **Tek buton adı**: "Kaydet ve Odayı Tasarla". Oda ismi tam ekran değil, tek alanlı küçük bir pencerede sorulur; boş bırakılırsa "Yeni Oda" (bugünkü davranış).
7. Bu ekrandaki **geliştirici yazıları** (`floor:parquet wall:paint warm`, `AI texture üretiliyor…` gibi) dış kullanıcıdan gizlenecek.

## Gerekçe
- Ölçü doğrulaması ürünün tek somut vaadini (gerçek ölçü) koruyan yer: RoomPlan'ın hatası (ör. TV'yi pencere sanması) Blender çıktısına aynen geçiyor. Kullanıcıya çıktıyı gizlemek hatayı düzeltmiyor, sadece yakalama şansını kaldırıyor.
- "Yeniden tara" yolu verilmezse yanlış ölçü tüm tasarımı bozar ve kullanıcı bunu ancak en sonda anlar.
- Tek buton kullanıcı için doğru; ama arkasında hâlâ birkaç adım olduğu için akışta fotoğraf adımlarının **butondan önce** durması gerekiyor.

## Değerlendirilen Alternatifler
- **Köşe fotoğraflarını isteğe bağlı yapmak / tamamen kaldırmak**: akış kısalır ama odanın gerçek zemini/duvarı kaybolur, aynı oda herkeste aynı görünür.
- **Doğrulama ekranında da Kat Planı|3D seçici**: karışıklığın ana kaynağı olurdu.

## Sonuçlar (Consequences)
- Tasarım ekranındaki üçüncü sekme ("Roomplan") kalkıyor.
- Doğrulama ekranı yeni bir ekran olarak yazılacak (bugün tarama sonrası akış farklı).

## Riskler
- Kullanıcı kaba taslak görünümü görüp uygulamadan çıkabilir; nottaki son cümle ("bir sonraki adımda çok daha gerçekçi olacak") tam bu riski azaltmak için var.

## İlgili Görevler
→ [[Task Board]]

## İlgili Bilgi
[[Room Scanning Overview]], [[30 Knowledge/Product/Product Flows|Product Flows (Knowledge)]]

## Kaynak Toplantı
[[2026 08 06 Thinking Session — Uygulama User Journey]]
