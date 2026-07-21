---
type: knowledge
status: living
updated: 2026-07-20
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
- Mobilya min-oran fit: GLB oranı üründen farklıysa mobilya küçük görünür; `widthCm` boşsa hiç ölçeklenmez.
- ARKit/RoomPlan pozları 3DGS eğitimi için **yetersiz** (COLMAP teşhisiyle kanıtlandı) — splat'a dönülürse bunu unutma. Bkz. [[Gaussian Splatting self-hosted gsplat]].
- Tarama sırasında ağır ek işlem (video kaydı, mesh, analiz) ısınma/crash yaratır — ağır işler tarama **bittikten sonra**.

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

## İlgili Notlar
[[System Architecture]], [[3D Render Pipeline]], [[Deployment Strategy]]

## Kaynaklar
`~/Desktop/livaro/PROJECT_STATUS.md`; [[2026-07-08 Oturum Import — Web Temelleri ve iOS Başlangıcı]]; [[2026-07-16 Oturum Import — 3D Pipeline Evrimi]]; [[2026-07-20 Oturum Import — Texture Pipeline ve Yakın Çekim]]
