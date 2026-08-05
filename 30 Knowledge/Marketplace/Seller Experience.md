---
type: knowledge
status: living
updated: 2026-08-05
related: []
---

# Seller Experience

## Şu An Bilinenler
- **3D bekleme deneyimi ve stok göstergesi tasarlandı ve KODLANDI (2026-08-05)** → [[2026 08 05 Thinking Session — Mağaza Paneli 3D İlerleme ve Stok Göstergesi]]. **Kod main'e merge edildi ve push edildi (`7d5ba06`, 468 test yeşil); canlı demo yerelde yapıldı, 3D görüntüleyici kurucu tarafından gerçek tarayıcıda doğrulandı. Gerçek satıcı hâlâ kullanmadı — Validated değil.** Uygulamada verilen iki küçük ek karar: (1) yüzde %100'e varınca kutucukta "Son hazırlıklar yapılıyor" yazar (Open Questions'taki %100 sorusunun pratik cevabı — kurucu isterse değişir); (2) süre ortalaması kategori bazında sayılır (20+ başarılı ölçüm o kategoride birikince). Ayrıca canlıda bulunan tutarsızlık: panel halı kalınlığına 0,1 cm izin veriyor ama sunucu 1 cm altını reddediyor — ayrı iş olarak işaretlendi.
  - **Bugünkü deneyim kırık (ölçüldü):** fotoğraf yüklenince tarayıcının `alert()` kutusu çıkıyor ("3D üretim başladı. Kalan hak: 1"), ürün listesine yönlendiriliyor. İlerleme yok, süre yok, liste kendiliğinden yenilenmiyor, **bitiş bildirimi hiç yok**. Ürünün "mağaza onayı bekliyor"da takılı kalmasının başlıca sebebi bu.
  - **İlerleme yüzdesi elde var ama kullanılmıyor:** Tripo3D iş durumu sorulduğunda 0-100 arası bir sayı gönderiyor; hiçbir yere kaydedilmiyor, panele gitmiyor.
  - **Süre hiç ölçülmemiş ve geriye dönük çıkarılamaz** (3D kaydı her denemede üzerine yazılıyor). Tek somut sayı bir **tavan**: arka plan işçisi Tripo'yu en fazla 5 dakika bekliyor (60 sorgu × 5 saniye), aşarsa zaman aşımı. Karar: önce "genelde birkaç dakika sürer", ölçüm başlar, 20 üretim sonra gerçek ortalama → [[2026-08-05 3D süre yazısı — önce tahmin, 20 üretim sonra gerçek ortalama]].
  - **İşler sırayla yapılıyor** (kuyrukta eşzamanlılık ayarı yok) — çok ürün gönderen mağazanın sonuncusu diğerlerinin arkasında bekler; bekleyene süre sözü verilmeyecek.
  - **İlerleme kutucuğu** panelin her sayfasında, kapatılabilir, kapatılınca üst çubukta iz; bitince yeşil "hazır — inceleyin"; hatada iki ayrı mesaj → [[2026-08-05 3D ilerleme göstergesi — her sayfada kapatılabilir kutucuk]].
  - **Deneme hakkı adaletsizliği bulundu ve düzeltilecek:** hak gönderim anında düşüyor, aynı fotoğraflarla tekrar deneme koda gömülü şekilde yasak ve başarısızlıkta iade yok — yani sistem kendi hatasıyla (zaman aşımı, çökme) patladığında hatası olmayan mağaza hem hakkını yakıyor hem yeniden fotoğraf çekmek zorunda kalıyor. Karar: sistem hatasında hak iade edilir, aynı fotoğraflarla tekrar denenebilir → [[2026-08-05 Sistem hatasında 3D deneme hakkı iade edilir]] (2026-07-28'deki 2-hak kuralını inceltir).
  - **Stok gerçeği:** mobilyada stok **hiç sorulmuyor** (`stocked: false`, bilinçli — sipariş üzerine üretim), stoklu kategoriler halı ve perde. Ürünü müşteriden gizleyen tek şey elle basılan "stokta yok" işareti; **stok adedi hiçbir yayın filtresine girmiyor**, yani bugün "Stok: 0" yazan ürün satışta kalıyor. Karar: stoklu kategoride sayı kutucuğu + sıfırda otomatik gizleme, mobilyada "Satışta / Satışta değil" anahtarı → [[2026-08-05 Stok göstergesi — stoklu kategoride sayı, mobilyada satışta anahtarı]].
  - **3D model ürün düzenleme sayfasına taşınıyor**, Onayla/Reddet dahil; ayrı "3D'yi İncele" sayfası kalkıyor → [[2026-08-05 3D model ve onay ürün düzenleme sayfasına taşınır]].
  - **Supabase edge function aynası deploy edildi (2026-08-05)**: stok kuralı iOS yayın sürümünün bağlandığı uçta da canlı doğrulandı (stok 0 → katalogdan düşüyor, tekil uç 404; kategorisiz/stoksuz kategoriler muaf; login yolu bozulmadı). Deploy anında düşen yayında ürün olmadı.
- **Mağaza web sitesi + yönetim (admin) sitesi main'e birleştirildi ve push edildi (2026-07-31, `44a4497`)** → [[2026-07-31 Kategori 3D Stratejisi, Tripo Kredi Ölçümü, iOS Doku Düzeltmesi ve Main Merge]]. Merge öncesi zorunlu Codex inceleme kapısı 7 turda 22 açık buldu (KVKK sızıntıları, eski `/3d-pipeline` ucundan 3D zorunluluğu/admin onayı atlatma, kredi çift yakma riskleri) — hepsi regresyon testiyle kapatıldı, 399 test yeşil. **Gerçek satıcı henüz kullanmadı — Validated değil.**
- **Mağaza web sitesi + yönetim (admin) sitesi build edildi, yerelde uçtan uca çalışıyor (2026-07-29)** → [[2026-07-29 Build Oturumu — Mağaza Web ve Yönetim Sitesi]]:
  - İki ayrı site: `web/` (mağaza/satıcı — herkese açık tanıtım/kayıt/giriş/panel) ve `admin/` (yalnız kurucular — başvurular/ürün onayı/takılanlar). Bu ayrım kurucu kararı (2026-07-28 sohbeti, kod reposu spec dokümanı). Admin'in bu turu **kasıtlı olarak asgari**; kapsamlı yönetim paneli (metrikler, kullanıcı yönetimi, içerik denetimi) ayrı bir **gelecek thinking session'da** tasarlanacak.
  - Uçtan uca akış yerelde canlı doğrulandı: kayıt → admin onayı → giriş (şifre; SMS sekmesi Supabase env boşken hiç görünmüyor, DOM'da yok) → ürün + 4 etiketli foto → 3D (fake modda) → mağaza 3D onayı → admin yayın onayı → herkese açık katalogda görünür + "stokta yok" işaretlenince listeden düşer.
  - **Fotoğraflar artık serbest çoklu-seçim değil, 4 ETİKETLİ slot** (ön/arka/sol/sağ) — hem `web/` hem `admin/`'de. Tripo'nun sıralı girdi beklediği ve Tripo'nun "sol"unun NESNENİN kendi solu olduğu (aynalı-model riski) build sırasında netleşince eklendi; çekim rehberi benzetme yerine mekanik tarifle yeniden yazıldı ("ön noktadan sağa yürü = Sol").
  - Yeni foto seti yüklenince eskisi silinir, üzerine eklenmez (kurucu kararı) → [[2026-07-29 Yeni fotoğraf seti eskisinin yerine geçer, tekil silme yok]].
  - Geride kalan gerçek entegrasyon sorunu: R2 bucket'ta CORS politikası yok, 3D model tarayıcıda yüklenmiyor — **ÇÖZÜLDÜ (2026-07-29 akşamı)**: kurucu Cloudflare panelinden CORS ekledi, canlı doğrulandı.
  - Eski `brand-panel/`'e bu turda dokunulmadı (yalnız referans); emekliye ayrılma kararı henüz verilmedi.
- **Kategori bazlı 3D üretim stratejisi (2026-07-29 akşamı)** → [[2026-07-29 Kategori bazlı 3D üretim stratejisi — halı düz yüzey, mobilya Tripo devam, perde sonraya]]:
  - **Halı: Tripo KULLANILMIYOR** — Tripo'suz düz yüzey + yüksek çözünürlüklü doku. Kanıt: aynı halı hem Tripo hem düz yüzeyle üretilip karşılaştırıldı, düz yüzey hem daha net hem 0 kredi (Tripo ~50-70 kredi).
  - **Halıda kalınlık artık 0,1 cm'den itibaren kaydediliyor (2026-08-05 düzeltmesi):** panel 0,1 cm'e izin verirken backend koşulsuz ≥ 1 cm dayatıyordu — gerçek bir halı (0,8 cm hav) canlıda hiç kaydedilemiyordu. Sınır artık kategoriye duyarlı: halı ≥ 0,1 cm (= 1 mm, düz ürün geometrisinin MIN_THICKNESS_MM kuralı), mobilya/perde ≥ 1 cm. Üç turlu Codex incelemesiyle main'e alındı → [[2026-08-05 Halı Kalınlık Doğrulaması Düzeltmesi]].
  - **Halı ölçüsü SAÇAK HARİÇ (2026-08-05 kararı):** satıcının girdiği en/boy halının dokuma alanıdır; saçak ürünün ölçüsünün dışında ayrı yassı şerit olarak modellenir. Eskiden saçak ölçünün içine sıkıştırılıyor ve desen boyuna %5-12 eziliyordu. Modelin gerçek kutusu (saçak dahil) ayrı alanlarla iOS'a taşınıyor → [[2026-08-05 Halı ölçüsü saçak hariç — saçak ayrı yassı şerit olarak modellenir]].
  - **Halı fotoğrafında BOŞLUK zorunlu (2026-08-06 kararı):** ürünün etrafında kenar başına en az %2 zemin görünmeli; kontrol YÜKLEME ANINDA yapılır, geçmeyen fotoğraf depoya hiç yazılmaz. İstisna: halıya birebir kırpılmış katalog görseli kabul edilir. Reddedilen, arada kalmış kırpımdır (kenarda birkaç piksel zemin artığı) — o fotoğrafta arka plan temizlenemiyor ve desen ~%10 geriliyor → [[2026-08-06 Düz üründe fotoğraf boşluğu zorunlu — birebir kırpım istisna]].
  - **Halı dokusundaki delik kusuru düzeltildi (2026-08-06):** krem bordür/beyaz çiçek gibi açık renkli alanlar 3D'de siyah çıkıyordu (dokunun %82'si delinmişti, delikten dilimin karanlık alt yüzü görünüyordu). Ölçüm: %82 → %0 → [[2026-08-06 Halı Doku Delikleri, Saçak Modeli ve Migration Kurtarması]].
  - **Mobilya: Tripo `multiview_to_model` devam**, model sürümü v3.1'e çekildi. Gerçek kredi ölçümü yapıldı: kullanılabilir kalitede model (4-5K üçgen, 4K doku) **60 kredi**'ye mal oluyor (30 kredilik "standart" ayar 1,4 milyon üçgen + 38,7 MB üretiyor, kullanılamaz) → [[Kategori bazlı 3D üretim denemeleri — halı Tripo vs düz yüzey, kanepe kredi-kalite ölçümü]].
  - **Perde: tedarik yolu henüz seçilmedi** — sonraya bırakıldı (aşağıda, Bilinmeyenler).
  - **Mobilyada ön/arka/sol/sağ → Tripo front/left/back/right eşlemesi hâlâ gerçek 4 açılı bir ürünle doğrulanmadı** — pilottan önce yapılmalı → [[Open Questions]].
- **iOS'ta doku haritaları düzeltildi (2026-07-29/30):** USDZ dönüştürücü daha önce yalnız renk dokusunu taşıyordu, normal/pürüzlülük/metaliklik haritalarını sessizce atıyordu (AR'da model düz görünüyordu). Ayrıca bir ölçek hatası (Tripo GLB node transform'u okunmuyordu) düzeltildi. Bkz. [[Known Pitfalls]].
- **Mağaza web paneli user journey kararlaştı (2026-07-28 thinking session)** → [[2026 07 28 Thinking Session — Mağaza Web Paneli User Journey]]:
  - **Kayıt (self-serve):** e-posta, telefon, ad-soyad, mağaza adı, şehir, ilçe, kategori(ler), şifre; KVKK + satıcı sözleşmesi onay kutuları; opsiyonel web sitesi/Instagram alanı; yasal belgeler (vergi levhası vb.) MVP'de yok. Kaydol → kuruculara e-posta → net beklentili "onaya gönderildi" ekranı → admin onayıyla hesap açılır (onay/red e-postası) → [[2026-07-28 Mağaza kaydı self-serve + admin onayı]].
  - **Giriş:** şifre veya telefona SMS kodu (ikisi de).
  - **Panel açılışı:** ilk günden boş metrik yerine ürün durumu (yüklendi / 3D bekliyor / yayında); metrikler veri birikince.
  - **Ürün ekleme:** ad, kategori, kategoriye özel sorular (setler hazır değil — ayrı session planlı), fiyat, ölçüler, stoklu kategorilerde stok; fotoğraflar + örnekli çekim rehberi. Ürün düzenleme/silme + "stokta yok" işaretleme var → [[2026-07-28 Ürün yükleme ve panel — 3D zorunlu, Tripo 2 hak]].
  - **3D:** Tripo3D arka planda; mağaza modeli web'de döndürerek inceler, Onayla/Reddet. 2 deneme hakkı; aynı fotoğraflarla tekrar engelli; 2 hak biterse admin kuyruğuna "takıldı" düşer. **3D zorunlu** — 3D'siz ürün katalogda kayıtlı ama yayında değil. Mağaza onayı sonrası **admin ürün onayı** → yayın.
  - **Excel toplu yükleme de olacak** (tekil için web formu).
  - **Sorular:** herkese açık (Trendyol benzeri); telefon/IBAN/link filtresi; yeni soruda mağazaya e-posta bildirimi. **Sohbet MVP'de yok**, sipariş/checkout ile → [[2026-07-28 Mağaza iletişimi — herkese açık sorular, sohbet MVP dışı]].
- **Thinking session güncellemeleri (2026-07-24)**:
  - **Tripo3D hattı devam** (kurucu teyidi; anlatımdaki "tripodla çekim" Tripo3D/tripod karışıklığıydı, tripod fikri yok).
  - **Pilot marka kriterleri kararlaştı**: internette satan, vizyoner, çeşitliliği yüksek firmalardan her kategoriden 2 tane; mağazalara MVP bitince gidilecek → [[2026-07-24 Pilot marka kriterleri]].
  - **Toplu ürün yükleme planı — Excel şablonu ONAYLANDI (teyit turu, 2026-07-24)**: pilot firmaların web sitesi fotoğrafları kullanılacak; taslak **Excel şablonu** (mağaza tüm özellikleri girer; fotoğraflar link sütunuyla bağlanır) veya **API** ile toplu yükleme. (PM uyarısı geçerli: site fotoğrafları Tripo3D'nin 4 açı formatı değil; önce 20 ürünlük kalite+maliyet denemesi önerisi masada → [[2026-07-24 PM Gözden Geçirme — Thinking Session]].)
  - **Stok**: mağazalar stoklu ürünlerde stok girecek; özel üretimde stok takibi yok.
  - **İstenen admin paneli metrikleri (vizyon)**: ürün görüntüleme, tıklanma sayısı, kaç kişinin ürünle tasarım yaptığı, sepete eklenme sayısı.
  - Kaynak: [[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu]] (cevap 5, 16, 30, 32).
- **Satıcı web paneli (brand-panel) prototipte mevcut** (Haziran, Faz 3): Vite + React Router; yalnızca SELLER/ADMIN rolleri girebilir (CUSTOMER engellenir). Kaynak: [[2026-07-08 Oturum Import — Web Temelleri ve iOS Başlangıcı]].
- **Ürün yükleme akışı çalışıyor** (brand-panel, Haziran): form (ad, açıklama, fiyat, **en/boy/yükseklik cm — üçü zorunlu** çünkü 3D model gerçek ölçülere göre scale ediliyor; kumaş opsiyonel) + 4 açı fotoğrafı (ön/arka/sol/sağ) isteniyordu. Kaydetme resumable state machine: ürün oluştur → fotoğrafları yükle → 3D pipeline tetikle; hatada "Tekrar dene" kaldığı adımdan sürer.
  - **DÜZELTME (2026-07-29):** Bu not daha önce burada "4 açı fotoğrafı Tripo3D multi-view 3D model üretiminin girdisi" diyordu — bu **yanlıştı**. Mağaza web + yönetim sitesi build oturumunun uçtan uca kabul turunda bulundu: kod Tripo'ya yalnızca İLK fotoğrafı gönderiyordu (`image_to_model`); satıcı 4 açı çekmesine rağmen model tek-fotoğraf kalitesinde üretiliyordu. Kurucu kararıyla (2026-07-29) düzeltildi: artık gerçekten 4 açının TAMAMI Tripo'nun `multiview_to_model` ucuna gönderiliyor → [[2026-07-29 3D üretimi 4 açının tamamını kullanır — Tripo multiview_to_model]]. Kayıt: [[2026-07-29 Build Oturumu — Mağaza Web ve Yönetim Sitesi]].
- slug/sku gibi teknik alanlar satıcıdan gizlenip otomatik üretiliyor. Markası olmayan satıcı ürün ekleyemez (bilinçli engelleme mesajı).
- Görsel kimlik: "Sıcak/Lüks" — koyu kahve-siyah #1C1917 + altın #A16207, dark-first, Inter (kurucu seçimi, 17-19 Haz).
- Maliyet notu: 3D pipeline retry'ı Tripo3D sonucunu cache'lemiyor — her "Yeniden dene" gerçek kredi harcar (bkz. [[Known Pitfalls]]). Mobilyada kullanılabilir kalite için gerçek maliyet artık ölçülü: **60 kredi/ürün** (bkz. yukarı, kategori bazlı strateji).
- brand-panel'in **güncel bakım durumu belirsiz**: Temmuz oturumları tamamen iOS/3D'ye odaklandı; panelin bu dönemde test edilip edilmediği **Needs Validation**.
- **iOS uygulaması bu turun KVKK sızıntı düzeltmesinden sonra Xcode'da bir kez derlenip test edilmedi** (`ios/Livaro/Models/Brand.swift`'te `ownerId` alanı opsiyonel yapıldı çünkü backend artık bu alanı herkese açık uçlarda döndürmüyor) — bkz. [[Open Questions]].

## Varsayımlar
- Satıcıların 4 açı fotoğrafı çekme zahmetine katlanacağı — **Needs Validation** (hiç gerçek satıcıyla test edilmedi).

## Bilinmeyenler
- Satıcıların kim olacağı (mağazalar, bireysel, üreticiler) — **Unknown**. Kurucu beyanı (2026-07-21): **satıcı adayı var, henüz görüşülmedi** (kaynak: [[2026-07-21 PM Panel Tartışması]]).
- ~~Satıcı onboarding'i (davet mi, self-serve mi)~~ — **ÇÖZÜLDÜ (2026-07-28)**: self-serve kayıt + admin onayı → [[2026-07-28 Mağaza kaydı self-serve + admin onayı]].
- Katalog import/entegrasyon ihtiyacı — **Unknown**.
- Başvuru onay/red kriterleri; Tripo aylık bütçesi; herkese açık soruların denetim kuralı; kategori soru setleri — **To Be Decided** → [[Open Questions]].
- **Perde tedarik yolu** (hazır kıvrımlı model kütüphanesi nasıl edinilecek — freelancer mı, hazır asset mi) — **To Be Decided** → [[2026-07-29 Kategori bazlı 3D üretim stratejisi — halı düz yüzey, mobilya Tripo devam, perde sonraya]], [[Open Questions]].
- **Mobilyada Tripo'nun ön/arka/sol/sağ eşlemesi gerçek 4 açılı bir ürünle doğrulanmadı** — **Needs Validation** → [[Open Questions]].

## Önemli Sorular
- Satıcı tarafı MVP'de mi? Katalog kim tarafından doldurulacak (ilk fazda ekip mi, satıcılar mı)?
- Tripo3D çıktı kalitesi gerçek mobilya çeşitliliğinde yeterli mi?

## İlgili Notlar
- [[Marketplace Model]], [[60 Planning/Product Flows|Product Flows]], [[2026-06-22 iOS uygulaması yalnızca müşteri tarafı]]
- [[Admin Panel]] — yönetim sitesinin durumu ve v1 tasarımı (2026-08-04 session) artık kendi notunda

## Kaynaklar
- [[2026-07-08 Oturum Import — Web Temelleri ve iOS Başlangıcı]]
- [[2026-07-29 Build Oturumu — Mağaza Web ve Yönetim Sitesi]]
- [[2026-07-31 Kategori 3D Stratejisi, Tripo Kredi Ölçümü, iOS Doku Düzeltmesi ve Main Merge]]
