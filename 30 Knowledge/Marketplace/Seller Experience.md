---
type: knowledge
status: living
updated: 2026-08-05
related: []
---

# Seller Experience

## Şu An Bilinenler
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
