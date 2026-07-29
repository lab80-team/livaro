---
type: knowledge
status: living
updated: 2026-07-29
related: []
---

# Seller Experience

## Şu An Bilinenler
- **Mağaza web sitesi + yönetim (admin) sitesi build edildi, yerelde uçtan uca çalışıyor (2026-07-29)** → [[2026-07-29 Build Oturumu — Mağaza Web ve Yönetim Sitesi]]:
  - İki ayrı site: `web/` (mağaza/satıcı — herkese açık tanıtım/kayıt/giriş/panel) ve `admin/` (yalnız kurucular — başvurular/ürün onayı/takılanlar). Bu ayrım kurucu kararı (2026-07-28 sohbeti, kod reposu spec dokümanı). Admin'in bu turu **kasıtlı olarak asgari**; kapsamlı yönetim paneli (metrikler, kullanıcı yönetimi, içerik denetimi) ayrı bir **gelecek thinking session'da** tasarlanacak.
  - Uçtan uca akış yerelde canlı doğrulandı: kayıt → admin onayı → giriş (şifre; SMS sekmesi Supabase env boşken hiç görünmüyor, DOM'da yok) → ürün + 4 etiketli foto → 3D (fake modda) → mağaza 3D onayı → admin yayın onayı → herkese açık katalogda görünür + "stokta yok" işaretlenince listeden düşer.
  - **Fotoğraflar artık serbest çoklu-seçim değil, 4 ETİKETLİ slot** (ön/arka/sol/sağ) — hem `web/` hem `admin/`'de. Tripo'nun sıralı girdi beklediği ve Tripo'nun "sol"unun NESNENİN kendi solu olduğu (aynalı-model riski) build sırasında netleşince eklendi; çekim rehberi benzetme yerine mekanik tarifle yeniden yazıldı ("ön noktadan sağa yürü = Sol").
  - Yeni foto seti yüklenince eskisi silinir, üzerine eklenmez (kurucu kararı) → [[2026-07-29 Yeni fotoğraf seti eskisinin yerine geçer, tekil silme yok]].
  - **main'e merge edilmedi, push edilmedi** — dal (`feature/store-web`, main'e göre 109 commit) kurucu incelemesini ve reponun zorunlu Codex inceleme kapısını bekliyor.
  - Geride kalan gerçek entegrasyon sorunu: R2 bucket'ta CORS politikası yok, 3D model tarayıcıda yüklenmiyor (onay/red akışı buna bağımlı değil) → [[Open Questions]].
  - Eski `brand-panel/`'e bu turda dokunulmadı (yalnız referans); emekliye ayrılma kararı merge aşamasında verilecek.
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
- Maliyet notu: 3D pipeline retry'ı Tripo3D sonucunu cache'lemiyor — her "Yeniden dene" gerçek kredi harcar (bkz. [[Known Pitfalls]]).
- brand-panel'in **güncel bakım durumu belirsiz**: Temmuz oturumları tamamen iOS/3D'ye odaklandı; panelin bu dönemde test edilip edilmediği **Needs Validation**.

## Varsayımlar
- Satıcıların 4 açı fotoğrafı çekme zahmetine katlanacağı — **Needs Validation** (hiç gerçek satıcıyla test edilmedi).

## Bilinmeyenler
- Satıcıların kim olacağı (mağazalar, bireysel, üreticiler) — **Unknown**. Kurucu beyanı (2026-07-21): **satıcı adayı var, henüz görüşülmedi** (kaynak: [[2026-07-21 PM Panel Tartışması]]).
- ~~Satıcı onboarding'i (davet mi, self-serve mi)~~ — **ÇÖZÜLDÜ (2026-07-28)**: self-serve kayıt + admin onayı → [[2026-07-28 Mağaza kaydı self-serve + admin onayı]].
- Katalog import/entegrasyon ihtiyacı — **Unknown**.
- Başvuru onay/red kriterleri; Tripo aylık bütçesi; herkese açık soruların denetim kuralı; kategori soru setleri — **To Be Decided** → [[Open Questions]].

## Önemli Sorular
- Satıcı tarafı MVP'de mi? Katalog kim tarafından doldurulacak (ilk fazda ekip mi, satıcılar mı)?
- Tripo3D çıktı kalitesi gerçek mobilya çeşitliliğinde yeterli mi?

## İlgili Notlar
- [[Marketplace Model]], [[60 Planning/Product Flows|Product Flows]], [[2026-06-22 iOS uygulaması yalnızca müşteri tarafı]]

## Kaynaklar
- [[2026-07-08 Oturum Import — Web Temelleri ve iOS Başlangıcı]]
- [[2026-07-29 Build Oturumu — Mağaza Web ve Yönetim Sitesi]]
