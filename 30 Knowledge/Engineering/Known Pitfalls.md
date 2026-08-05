---
type: knowledge
status: living
updated: 2026-08-05
related: []
---

# Known Pitfalls (Bilinen Tuzaklar)

> Gelecekte zaman kaybettirmemesi için biriktirilmiş dersler. Kaynak: kod reposu `PROJECT_STATUS.md` + oturum import'ları. Her madde gerçekten yaşanmış bir sorundur.

## iOS / Swift
- **SIGTRAP crash**: UIViewController içindeki `static func` @MainActor'dır — arka plan kuyruğundan çağrı Swift 6 runtime denetiminde çöker. Çözüm: `nonisolated`. Teşhis için `python3 -m pymobiledevice3 crash pull` ile .ips çekmek çok işe yaradı.
- **CGContext UB**: `CGContext(data: &array, ...)` işaretçisi çağrı sonrası geçersiz — kullanım `withUnsafeMutableBytes` bloğu içinde olmalı.
- **Dealloc yarışı**: RoomPlan `didPresent` → SwiftUI VC'yi söker → `[weak self]` callback'ler düşer. Çözüm: VC'den bağımsız `@MainActor FrameCaptureSink`.
- **print() devicectl konsolunda görünmez** — NSLog/os_log kullan.
- Yeni Swift dosyası eklerken `cd ios && xcodegen generate` şart (proje pbxproj üretimli).
- Render bozuksa önce **veriyi** kontrol et: eski taramalarda `transform`/`dimensions` eksik → yeniden tarama gerekir; render koduna dokunma. Bkz. [[2026-07-09 3D render saf Transform matrix kullanır]].

## Backend / altyapı
- **Panel–DTO doğrulama kayması**: aynı sınır iki katmanda ayrı yazılınca ayrıştı — panel halıda 0,1 cm kalınlığa izin verirken DTO'daki koşulsuz `@Min(1)` gerçek bir halıyı (0,8 cm hav) canlıda hiç kaydettirmiyordu (5 Ağu, canlıda doğrulanıp düzeltildi). Kural: sınır tek sabitten türetilir (`FLAT_MIN_HEIGHT_CM` = `MIN_THICKNESS_MM`); kategoriye duyarlı kısım serviste, çünkü update gövdesinde kategori olmayabilir → [[2026-08-05 Halı Kalınlık Doğrulaması Düzeltmesi]].
- **PartialType/IsOptional açık `null`'u doğrulamadan geçirir** ve `{ ...dto }` DB'ye gerçekten NULL yazar; `??` ile null'u "gönderilmedi" saymak yanlış dalları açar (ölçülerek doğrulandı). Ayrıca panel her kaydetmede TÜM alanları gönderdiğinden "değişmemiş" alan aslında okuma anının bayat kopyasıdır — koşulsuz geri yazılırsa araya giren eşzamanlı güncellemeyi sessizce eski değere döndürür. Çözüm deseni: okunan değerle aynı gelen bağlayıcı alanları yazımdan çıkar + CAS koşuluna doğrulamanın dayandığı okunan alanları ekle (Codex 2 turda buldu) → [[2026-08-05 Halı Kalınlık Doğrulaması Düzeltmesi]].
- **Ham R2 URL'leri telefonda 401 verir** (bucket public değil): "Header start missing" hatası, kutu kalan mobilyalar hep bundandı. Kural: iOS'a giden her R2 URL'si `presignGet` ile.
- **Upstash Redis kotası** (500K istek) dolunca backend auth istekleri çöker → dev'de `REDIS_URL="redis://localhost:6379"`.
- **nest --watch**: proje köküne geçici `.ts` dosyası oluşturmak watch'ı tetikler (HTTP 000). DB/R2 kontrol script'leri için `.cjs` / inline `node -e` kullan.
- `.env` değişince nest watch **yeniden başlatılmalı**.
- **Replicate**: yeni hesapta kredi şart (402); eşzamanlılık düşük → istekler 2'şerli sıralı + retry + `Promise.allSettled`.
- DB kolonları camelCase — SQL'de quoted yazılmalı (`"createdAt"`).
- **Mac IP drift** (çözüldü): APIConfig artık mDNS `http://Selim-MacBook-Air.local:3000/api` kullanıyor; `NSLocalNetworkUsageDescription` gerekli. mDNS çalışmayan ağda fallback: `ipconfig getifaddr en0`.

## 3D / render
- **atan2/segment türetme yasak** — her denemede modeli bozdu (bkz. karar notu).
- **Dollhouse**: dıştan kamerada duvarlar içi kapatır → kameraya bakan duvarları o render'da gizle + `film_transparent`.
- **Texture pipeline hassas**: kapı fix'i gibi ilgisiz görünen değişiklikler texture yolunu bozdu ("zemin yine kahverengi", 18 Tem, iki kez). Değişiklik sonrası R2'deki `floor.jpg` içeriği ve backend log'u ("fotoğraftan kırpıldı [floor]") doğrulanmalı.
- **RoomPlan yanlış algı**: büyük TV/ekran pencere sanılabiliyor — model çıktısında olmayan cam panel görülürse önce RoomPlan verisindeki `windows` dizisine bak.
- Mobilya ölçekleme: GLB, ürünün cm kutusuna eksen bazlı ayrı ayrı gerilerek (non-uniform stretch) oturtulur — "min-oran uniform fit" değil (2026-07-31'de düzeltilen yanlış vault bilgisi, bkz. [[System Architecture]]); GLB oranı üründen farklıysa model üç eksende de distorte olabilir. `widthCm` boşsa hiç ölçeklenmez.
- **Arka plan silme SALT RENKLE yapılırsa ürünün açık renkli yerlerini deler**: düz ürün boru hattı saçak boşluklarını "zemine renk olarak yakın piksel saydam olsun" diye açıyordu; krem bordürlü halıda dokunun **%82'si delik** oldu (ölçüldü). Delikten dilimin ALT yüzü görünüyor ve ışığa sırtı dönük olduğu için SİYAH render ediliyor — kurucu bunu "bordür siyah çıkmış" diye bildirdi. Üç kanıt katmanı gerekti: renk karakteri (gölge kanalları EŞİT düşürür, krem iplik EŞİTSİZ kaydırır), iki eşikli bağlantı (zayıf piksel ancak çekirdeğe DEĞİYORSA ürün), ve topolojik delik doldurma (ürünün içinde dışarıdan ulaşılamayan piksel saydam olamaz). Ders: "zemine benziyor" bir RENK ölçüsü değil, bir TOPOLOJİ+KARAKTER sorusudur. Bkz. [[2026-08-06 Halı Doku Delikleri, Saçak Modeli ve Migration Kurtarması]].
- **Test fixture'ları kusurun yaşandığı kombinasyonu içermiyorsa kusur testten kaçar**: yukarıdaki delik hatası aylarca yakalanmadı çünkü sentetik halılarda ya bordür koyuydu ya halının tamamı açıktı; kırılan durum **"açık bordür + koyu zemin"**di ve hiç kurulmamıştı. Yeni bir kusur sınıfı bulununca önce onu ÜRETEN fixture yazılmalı.
- **USDZ dönüştürücü yalnız renk dokusunu taşıyabilir**: `glb_to_usdz.py` bir süre yalnız renk (albedo) dokusunu aktarıyor, normal/pürüzlülük/metaliklik haritalarını sessizce atıyordu — sonuç derlenip çalışıyor ama AR'da model "düz" görünüyordu (hiçbir hata/uyarı yok). Bu sınıf kayıp dosyanın hiç testi olmadığı için fark edilmemişti (30 Tem'de ilk testler eklendi). Ders: bir 3D dönüştürücünün "çalıştığını" doğrulamak yetmez — hangi PBR haritalarının gerçekten taşındığı ayrıca doğrulanmalı.
- ARKit/RoomPlan pozları 3DGS eğitimi için **yetersiz** (COLMAP teşhisiyle kanıtlandı) — splat'a dönülürse bunu unutma. Bkz. [[Gaussian Splatting self-hosted gsplat]].
- Tarama sırasında ağır ek işlem (video kaydı, mesh, analiz) ısınma/crash yaratır — ağır işler tarama **bittikten sonra**.

- **Migration SQL'i ELLE YAZILMAZ**: Prisma model adı ile tablo adı farklı olabilir (`model ThreeDModel` + `@@map("three_d_models")`). Elle yazılan bir migration model adını kullandı, canlıda `relation "ThreeDModel" does not exist` ile patladı ve Prisma başarısız migration'ı kaydettiği için **sonraki TÜM migration'lar bloke oldu**. Kurtarma: `migrate resolve --rolled-back` + düzeltilmiş `migrate deploy`. Bu hatayı ne testler ne tip kontrolü yakalar — `.sql` dosyasına hiçbiri bakmıyor. Doğrusu `prisma migrate dev`: SQL'i şemadan türetir. Bkz. [[2026-08-06 Halı Doku Delikleri, Saçak Modeli ve Migration Kurtarması]].

## Güvenlik / API (24 Tem overhaul dersleri)
- **Presign oracle**: gelen herhangi bir URL'nin pathname'ini körlemesine imzalamak, R2'deki KEYFÎ nesne için imza dağıtan bir oracle oluşturur (satıcı, DTO'ya sahte host + bilinen key yazıp imzalı URL alabilirdi — Codex buldu). Kural: yalnız `R2_PUBLIC_URL` prefix'iyle başlayan URL imzalanır; eşleşmeyen olduğu gibi döner.
- **Supabase Edge Functions varsayılanı platform JWT doğrulaması**: custom auth kullanan function'da `config.toml` içinde `verify_jwt=false` olmalı, yoksa register/login istekleri handler'a hiç ulaşmaz.
- **Ayna tutarlılığı elle yaşamaz**: Nest ↔ edge function davranış farkları (rol sabitleme, şifre doğrulaması, JWT süresi) sessizce birikti; ayna dosyasına dokunan her değişiklikte iki taraf yan yana gözden geçirilmeli.
- **jest fake timers + sharp** thread pool'u kilitliyor — retry beklemelerini fake timer yerine `setTimeout` spy'ıyla atla.

## Web / backend (Haziran dönemi dersleri)
- **Tripo3D retry kredi yakar**: pipeline retry mekanizması Tripo3D sonucunu cache'lemez — her "Yeniden dene" gerçek paralı yeni çağrıdır. Dev'de `POST /3d-pipeline` mock DEĞİL: gerçek Tripo3D + R2 harcar.
- **XcodeGen `info:` tuzağı**: yalnızca `path:` verilirse her `xcodegen generate` Info.plist'i yeniden yazar ve özel key'leri (ör. load-bearing `NSAllowsLocalNetworking`) sessizce siler — `info.properties` bloğu şart.
- **Tailwind v4**: `bg-[--x]` köşeli parantez sözdizimi sessizce şeffaf renk üretir (var() sarmalanmaz) — doğrusu `bg-(--x)`. Bir kez 101 yerde düzeltildi.
- **ts-node + Prisma 7 generated client uyumsuz** ("Cannot find module ./internal/class.js") — standalone script'lerde `pg.Client` kullan.
- **`Product.id` Postgres'te text, uuid değil** — raw SQL'de `::uuid` cast'i sessiz hata üretir.
- **Postgres**: SELECT alias'ı ORDER BY içindeki ifadede çözülmez (42703) — alt sorguya sar.
- **Filtresiz `GET /products` DRAFT/ARCHIVED da döndürür** — iOS her istekte `status=PUBLISHED` gönderir (workaround).
- Swagger doğru yol: `/docs` (`/api/docs` 404).
- **Upstash REDIS_URL**: yalnızca URL, TLS için şema `rediss://` (redis-cli komutunu yapıştırma; log'a şifre sızdırdı — rotate önerildi, yapıldığı doğrulanmadı).
- Kayıt endpoint'i bir dönem `role:"ADMIN"` ile yetki yükseltmeye açıktı — 20 Haz denetiminde kapatıldı; benzer değişikliklerde rol whitelist'ini unutma.
- macOS'ta `/usr/bin/python3` Xcode python3'üne symlink — pxr/usd-core gibi paketler için hangi python'a kurulduğuna dikkat.
- `nest start --watch` `nest-cli.json` assets kopyalamayı çalıştırmaz (+`deleteOutDir:true` her başlatmada siler) — `.py` yardımcı script'leri dist'te kaybolabilir.

## Mağaza paneli / 3D bekleme (5 Ağu tasarım turunda kodda ölçüldü)
> Hepsi kodda doğrulandı, hiçbiri henüz düzeltilmedi → [[2026 08 05 Thinking Session — Mağaza Paneli 3D İlerleme ve Stok Göstergesi]].
- **Süre ölçümü hiç yok ve geriye dönük çıkarılamaz**: 3D kaydı her denemede öncekinin üstüne yazılıyor, yani "kaç dakika sürüyor" sorusunun cevabı geçmiş veriden türetilemez. Ders: bir işin süresini ileride göstermek isteyeceksen, ölçümü **iş çalışırken** başlat — sonradan telafisi yok.
- **Deneme hakkı sistem hatasında da yanıyor**: hak gönderim anında düşüyor, aynı fotoğraf setiyle tekrar gönderim `lastImageSetHash` ile engelli, başarısızlıkta iade yok. Zaman aşımı (5 dk tavan) veya çökme olursa hatası olmayan satıcı iki kez cezalandırılıyor. Ders: "deneme hakkı" sayacı kullanıcının hatasıyla sistemin hatasını ayırt etmeli.
- **Dış servisin yüzdesi işin tamamı değil**: Tripo'nun 0-100'ü yalnız model üretimi adımını anlatıyor; sonrasında indirme, gerçek cm ölçüsüne büyütme, USDZ'ye çevirme ve depoya yükleme var. Ham yüzdeyi olduğu gibi göstermek "%100'de donan ekran" üretir.
- **Sonucu iki ayrı tabloya yazan iş, yazımlardan biri kalıcı olarak düşerse sessiz veri kaybı üretir** (5 Ağu Codex bulgusu): 3D sistem hatasında hak iadesi ürün köprüsüyle aynı yazımdaydı; kalıcı bir DB kesintisinde kuyruğun üç denemesi de düşerse iade hiç uygulanmıyor, satıcının hakkı yanmış kalıyordu. Ders: böyle bir iş için kurtarma yolunda (bu işte admin retry3D) "bekleyen işi tamamla" adımı olmalı — ve o adımın çifte uygulanmayacağı satırdaki izden kanıtlanmalı (burada: başarılı iade ürünü DRAFT'a çekiyor, yani iz ancak iade uygulanmamışsa oluşuyor).
- **Paylaşılan Prisma `where` parçasını çıplak `OR` olarak spread etmek, çağıranın kendi `OR`'unu sessizce ezer** (5 Ağu Codex bulgusu). Ortak filtreleri sabit yerine **fonksiyon** olarak verin (`withInStock(where)`) ve koşulu `AND` dizisine ekleyin; çağıranın `AND`/`OR` anahtarları korunur.
- **React'te "unmount oldu mu" kontrolü oturum değişimini YAKALAMAZ** (5 Ağu Codex bulgusu): token değişince temizlik bayrağı false yapar ama yeni effect hemen true'ya çeker; eski token'la yola çıkmış istek dönüp YENİ kullanıcının ekranına eski kullanıcının verisini yazabilir. Her isteği kendi sırası + kendi token'ıyla eşleştirin ve oturum değişiminde listeyi temizleyin.
- **Stok adedi hiçbir yayın filtresine girmiyor**: ürünü müşteriden gizleyen tek koşul elle basılan `outOfStock` işareti (filtre en az beş yerde tanımlı: ürün, marka, kumaş, AI tasarım servisleri + Supabase ayna fonksiyonu). "Stok: 0" yazan ürün satışta kalıyor. Ders: aynı iş kuralı beş dosyaya kopyalanmışsa, birini güncelleyip diğerlerini unutmak sessiz bir tutarsızlık üretir.

## NestJS / TypeScript (29 Tem mağaza paneli build)
- **`ParseFilePipe` + `FileFieldsInterceptor` uyumsuz**: `ParseFilePipe`, `FileFieldsInterceptor`'ın çoklu-alan (obje) şeklini anlamıyor ve İÇERİKTEN BAĞIMSIZ olarak HER yüklemeyi sessizce reddediyor. Etiketli çoklu-foto yüklemede (ör. ön/arka/sol/sağ slotları) `ParseFilePipe` kullanmayın — özel bir validation pipe yazın (bu turda `ValidateLabeledPhotosPipe` ile çözüldü, canlıda yakalandı).
- **`tsconfig` `extends`, `exclude` dizilerini birleştirmiyor**: alt dosyanın `exclude`'u üst (`extends` edilen) dosyanınkini override eder, birleştirmez. Yeni bir alt-uygulama (ör. `web/`, `admin/`) eklerken hem `tsconfig.json` HEM `tsconfig.build.json`'a ayrı ayrı exclude eklenmeli — yalnız birine eklemek kök `nest build`'i (ve dolayısıyla önceki tüm görevlerin dayandığı derleme kapısını) sessizce kırar. Bu turda Task 13'te canlı yaşandı.

## Süreç / Kod İncelemesi (31 Tem main merge dersi)
- **Görev-bazlı inceleme eski kapıları görmez.** Mağaza web sitesi dalı main'e birleştirilirken (2026-07-31) her ajanın yalnız kendi diff'ine baktığı görev-bazlı incelemeler, "Haziran'dan kalma eski kapılar hâlâ açık mı?" sorusunu HİÇ sormamıştı — bu yüzden yeni build tamamlanana kadar şu açıklar fark edilmedi: satıcı eski `POST /products` ucundan `status:PUBLISHED` göndererek 3D zorunluluğu + admin onayını atlayabiliyordu; eski `/3d-pipeline` ucu satıcıya açık ve hak sayacına kör kalmıştı (sınırsız ücretli Tripo üretimi riski); `GET /brands` kimliksiz tüm marka satırını (telefon, red gerekçesi dahil) döndürüyordu (KVKK). Merge öncesi ayrı, bütüne bakan bir Codex turu (7 tur, 22 bulgu) bunları yakaladı. **Ders**: özellik bazlı/görev bazlı incelemeye ek olarak, main'e birleştirmeden önce "bu değişiklik eski/kullanılmayan uçları es geçiyor mu, onlar hâlâ ulaşılabilir mi" sorusunu soran ayrı, bütünsel bir güvenlik/sızıntı turu şart — tek başına iyi task-scoped review'lar bunu yakalamıyor. Detay: [[2026-07-31 Kategori 3D Stratejisi, Tripo Kredi Ölçümü, iOS Doku Düzeltmesi ve Main Merge]].

- **Testi zayıflatarak kusuru geçiştirme tuzağı (6 Ağu, kendi hatası olarak kaydedildi).** Halı ön kontrol testi yazılırken sentetik sahne beklenmedik şekilde GEÇTİ; doğru refleks kontrolü düzeltmekti, bunun yerine test sahnesi değiştirildi. Aynı açığı Codex bağımsız olarak buldu. **Ders**: bir test beklenmedik şekilde geçiyorsa önce "kontrol mü yetersiz" diye bakılır; sahneyi değiştirmek en son seçenektir ve gerekçesi yazılmalıdır. İkinci bir işaret: testin ADI yaptığı işi anlatmıyorsa (ör. "oran korunuyor" diyen bir testte kadraj kare) test yalan söylüyordur.

## İlgili Notlar
[[System Architecture]], [[3D Render Pipeline]], [[Deployment Strategy]]

## Kaynaklar
`~/Desktop/livaro/PROJECT_STATUS.md`; [[2026-07-08 Oturum Import — Web Temelleri ve iOS Başlangıcı]]; [[2026-07-16 Oturum Import — 3D Pipeline Evrimi]]; [[2026-07-20 Oturum Import — Texture Pipeline ve Yakın Çekim]]; [[2026-07-29 Build Oturumu — Mağaza Web ve Yönetim Sitesi]]; [[2026-07-31 Kategori 3D Stratejisi, Tripo Kredi Ölçümü, iOS Doku Düzeltmesi ve Main Merge]]
