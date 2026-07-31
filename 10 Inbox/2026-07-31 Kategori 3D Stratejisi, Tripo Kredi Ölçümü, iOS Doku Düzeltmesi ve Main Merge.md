---
type: import
date: 2026-07-31
status: processed
related: ["[[2026-07-29 Build Oturumu — Mağaza Web ve Yönetim Sitesi]]", "[[2026-07-29 3D üretimi 4 açının tamamını kullanır — Tripo multiview_to_model]]", "[[2026-07-29 Yeni fotoğraf seti eskisinin yerine geçer, tekil silme yok]]"]
---

# Kategori 3D Stratejisi, Tripo Kredi Ölçümü, iOS Doku Düzeltmesi ve Main Merge (29-31 Temmuz 2026)

> Kaynak: kod reposu (`~/Desktop/livaro`), `.superpowers/sdd/progress.md` (ilerleme defteri) + git commit geçmişi (dal `feature/store-web`, main'e `44a4497` ile birleşti). Bu not, [[2026-07-29 Build Oturumu — Mağaza Web ve Yönetim Sitesi]] notunun kapsadığı Task 1-26 build oturumunun **devamındaki** ayrı bir araştırma + karar + birleştirme turunu kaydediyor: kategori bazlı 3D stratejisi, gerçek Tripo kredi ölçümleri, iOS'ta kaybolan doku haritalarının düzeltilmesi ve dalın main'e birleştirilmesi. Ayrı not olarak açıldı çünkü 07-29 Build Oturumu notu belirli bir işe (Task 1-26 + RUNBOOK) odaklıydı; bu turun konusu farklı (araştırma + kalite/maliyet kararları + birleştirme).

## 1. Kategori bazlı 3D stratejisi (2026-07-29 akşamı)

Üç kollu araştırma (Tripo'nun resmi API dokümanı, sektör pratiği, kendi kodumuz) + gerçek yan yana deneme sonucu üç kurucu kararı:

- **Halı: Tripo KULLANILMAYACAK.** Düz yüzey + yüksek çözünürlüklü doku. Kanıt: aynı Hereke halısı hem Tripo hem düz yüzeyle üretilip yan yana karşılaştırıldı — düz yüzeyde desen fotoğraf kadar net, Tripo'da bulanık; maliyet 0 kredi vs ~50-70 kredi.
- **Mobilya: Tripo multiview devam**, model sürümü v2.5'ten (hiç gönderilmiyordu, sessiz varsayılan) v3.1'e çekildi.
- **Perde: SONRAYA BIRAKILDI.** Perdenin şekli ÜRÜNÜN değil ODANIN özelliği (korniş yüksekliği, pencere genişliği, bolluk); sektör hazır kıvrımlı mesh + kumaş giydirme kullanıyor. Araştırma yapıldı (`.superpowers/sdd/perde-3d-varlik-arastirmasi.md`): 10 modellik başlangıç seti önerisi, freelancer $500-1500/3-5 hafta, lisanslar uygun ama "kumaş değiştirilebilir UV" satın almadan bilinemiyor (asıl risk), tül perdede RealityKit saydamlık sıralama riski. **Tedarik yolu seçilmedi — açık.**

Detay ve gerekçe: [[2026-07-29 Kategori bazlı 3D üretim stratejisi — halı düz yüzey, mobilya Tripo devam, perde sonraya]]. Deney kaydı: [[Kategori bazlı 3D üretim denemeleri — halı Tripo vs düz yüzey, kanepe kredi-kalite ölçümü]].

## 2. Gerçek Tripo kredi ölçümleri — dokümanı yalanlayan bulgular

Aynı kanepe, aynı fotoğraflar, dört ayar denendi (kurucu onayıyla gerçek kredi harcandı). Tripo'nun kendi bildirdiği `consumed_credit` sonuçları:

| Ayar | Kredi | Üçgen | Doku | Dosya |
|---|---|---|---|---|
| v3.1 standart+standart | 30 | 1.378.939 | 2K | 38,7 MB (kullanılamaz) |
| v3.1 detaylı+detaylı | 60 | 4.683 | 4K | 4,5 MB |
| v3.0 detaylı+detaylı | 60 | 4.815 | 4K | 4,9 MB |
| P1 (en yeni) detaylı doku | 60 | 4.735 | 4K | 4,9 MB |

Kritik bulgular: (a) "ucuz" ayar bir tuzak — detaylı geometri modeli 1,4 milyondan 4.700 üçgene indiriyor, yani +20 kredi modeli KULLANILABİLİR kılıyor; (b) Tripo dokümanı P1 için "her şey dahil 50 kredi, ek ücret yok" diyordu — **gerçekte 60 çıktı, doküman yanlış**; (c) üç pahalı seçenek teknik olarak neredeyse aynı, seçim görsel tercihe kalıyor. **8K doku YOK** (üç bağımsız kanıtla doğrulandı — parametre yok, "detailed" zaten 4K'ya yükseltiyor, Tripo'nun dönüştürücüsünde 4096 tavan); zaten işimize yaramazdı — Apple'ın AR Quick Look tavsiyesi 2048×2048, biz 4096 gönderiyoruz.

Detay: [[Kategori bazlı 3D üretim denemeleri — halı Tripo vs düz yüzey, kanepe kredi-kalite ölçümü]].

## 3. iOS'ta kaybolan doku haritaları — düzeltildi

USDZ dönüştürücümüz (`src/three-d-pipeline/usdz/glb_to_usdz.py`) modelin yalnız renk dokusunu taşıyordu; **normal (yüzey kabartma) ve pürüzlülük/metaliklik haritalarını atıyordu** — yani telefonda AR'da model düz görünüyordu, 4K↔8K tartışmasından çok daha büyük bir görsel kayıp. Düzeltildi (tüm PBR haritaları + alfa + doku sarma modu + node/sahne ağacı gezme; ilk testleri yazıldı — dosyanın önceden hiç testi yoktu).

Ayrıca dönüştürücünün **ÖLÇEK hatası** bulundu ve düzeltildi: kanepe modeli USDZ'de 325×76×96 cm yerine 32,8×26,5×100 cm çıkıyordu (Tripo'nun GLB'sindeki node/scene transform'u dönüştürücü okumuyordu). iOS uygulamasında görünmüyordu çünkü `ModelLoader.swift` modeli zaten kendi ölçüsüne yeniden ölçekliyor — ama AR Quick Look / paylaşılan USDZ dosyası / ileride web AR için yanlıştı.

Commit'ler: `4717476`, `d0a31ca`, `bbf0982`, `804d351`, `42b17dd`, `16ba2a4`, `11c5dde` (2026-07-29 22:15 – 2026-07-30 17:07).

**Ayrıca kod incelemesinden çıkan düzeltilecek yanlış bilgi:** [[System Architecture]] notu 3D modelin "min-oran uniform fit" ile ölçeklendiğini söylüyordu; kod aslında her eksende (x/y/z) ayrı ayrı gerilme (non-uniform stretch) yapıyor (`ModelLoader.swift`: `loaded.scale = [size.x/ext.x, size.y/ext.y, size.z/ext.z]`). Vault'ta düzeltildi (bu turda).

## 4. Main'e birleştirildi — Codex kapısı 7 turda 22 açık buldu

Dal main'e birleştirildi ve push edildi (`44a4497`, 2026-07-31 18:43). 399 test yeşil, dört derleme (backend/web/admin/iOS ayrı ayrı doğrulanmış derlemeler — bkz. RUNBOOK ve progress defteri) temiz. Edge function deploy edildi ve canlı doğrulandı.

**Codex incelemesi kritik bir örüntü ortaya çıkardı:** görev-bazlı incelemeler (her ajan yalnız kendi diff'ine bakıyordu) main'e birleştirme öncesinde "Haziran'dan kalma eski kapılar hâlâ açık mı?" sorusunu HİÇ sormadı. En ciddi bulgular:

- Satıcı, eski `POST /products` ucundan `status: PUBLISHED` göndererek 3D zorunluluğunu ve admin onayını tamamen atlayabiliyordu.
- Eski `/3d-pipeline` ucu satıcıya açıktı ve hak sayacına bakmıyordu → sınırsız ücretli Tripo üretimi mümkündü.
- **KVKK:** `GET /brands` kimliksizdi ve tüm marka satırını döndürüyordu → onaylanmamış/reddedilmiş başvuruların telefonu, şehri/ilçesi ve red gerekçeleri internete açıktı. Aynı sızıntı ürün ve kumaş uçlarındaki gömülü marka üzerinden de vardı (commit `738fa5d`).
- Herkese açık tekil ürün ucu yayınlanmamış ürünleri sızdırıyordu (commit `54005b5`).
- Kuyruk işi yeniden teslim edilirse Tripo kredisi iki kez yanıyordu; parası ödenmiş BAŞARILI bir üretim sonraki bir hata yüzünden çöpe gidiyordu; ürün "üretiliyor" durumunda sessizce kaybolabiliyordu (kimse kurtaramıyor) (commit `6386dd0`, `629e2a0`).
- Ürün ADMIN_REJECTED'da çıkmaza girebiliyordu (commit `4c6dc88`).

Hepsi regresyon testi + mutasyon kanıtıyla kapatıldı. Turların gidişi: 7→3→5→4→1→1→0.

**Yapısal karar:** Kullanılmayan `/3d-pipeline` HTTP uç katmanı TAMAMEN SİLİNDİ (web/, admin/, iOS hiçbiri kullanmıyordu; tek çağıran uykudaki brand-panel prototipiydi). 3D üretim motoru (kuyruk, Tripo servisi, dönüştürücüler, düz yüzey üreticisi) duruyor. Gerekçe: kullanılmayan kodu sertleştirmek yerine kaldırmak. Detay: [[2026-07-31 Kullanılmayan 3d-pipeline HTTP uçları tamamen kaldırıldı]].

## 5. Açık kalanlar / sonraki işler

- **AI aramada oda taraması sahiplik kontrolü YOK** — giriş yapmış herhangi bir kullanıcı başkasının `roomScanId`'sini gönderip ev geometrisini alabiliyor ve o veri OpenAI'a gidiyor. Temmuz'dan kalma kod; kurucu kararıyla bu turun kapsamı dışında bırakıldı, AYRI İŞ olarak işaretlendi. **Pilottan önce kapatılmalı.**
- **Blender render mükerrer tetikleme koruması atomik değil** — aynı render birden çok kez ücretli koşabilir. Ayrı iş olarak işaretlendi.
- **iOS Xcode'da derlenmedi**: KVKK sızıntı düzeltmesi (`738fa5d`) `ios/Livaro/Models/Brand.swift`'te `ownerId` alanını opsiyonel yaptı (backend artık bu alanı döndürmüyor). Bir kez derlenip test edilmeli.
- Kalan artık riskler (Codex "merge-engeli değil" dedi): çökme anına denk gelen milisaniyelik pencereler; "sadece köprüyü tekrar dene" admin aksiyonunun olmaması.
- Perde tedarik yolu seçilmedi (bkz. bölüm 1).
- Mobilyada sol/sağ eşleme doğrulaması (gerçek 4 açıyla) hâlâ yapılmadı — halı denemesi bunu ölçemedi (bkz. bölüm 1 riskleri).

## İşlendiği notlar

[[Current State]], [[Open Questions]], [[Seller Experience]], [[60 Planning/Product Flows|Product Flows]], [[Known Pitfalls]], [[System Architecture]], [[Marketplace Model]], [[Decision Index]], [[Experiment Index]]
