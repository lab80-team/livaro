---
type: decision
status: accepted
created: 2026-07-31
source: "[[2026-07-31 Kategori 3D Stratejisi, Tripo Kredi Ölçümü, iOS Doku Düzeltmesi ve Main Merge]]"
related: ["[[Known Pitfalls]]", "[[System Architecture]]"]
---

# Kullanılmayan /3d-pipeline HTTP uçları tamamen kaldırıldı

## Bağlam
Mağaza web sitesi + yönetim sitesi dalının main'e birleştirilmeden önceki Codex inceleme turlarında (2026-07-31), eski `/3d-pipeline` HTTP uç katmanının (Haziran'dan kalma, brand-panel prototipi için yazılmış uçlar) hâlâ satıcıya açık olduğu ve yeni mağaza web sitesindeki güvenlik/hak kontrollerini (3D zorunluluğu, admin onayı, Tripo hak sayacı) atlattığı bulundu — bkz. [[2026-07-31 Kategori 3D Stratejisi, Tripo Kredi Ölçümü, iOS Doku Düzeltmesi ve Main Merge]].

Bu, "görev-bazlı incelemenin eski kapıları görmediği" örüntüsünün somut örneği: her ajan yalnız kendi diff'ine baktığı için "Haziran'dan kalma eski kapılar hâlâ açık mı?" sorusu hiç sorulmamıştı.

## Karar
Kullanılmayan `/3d-pipeline` HTTP uç katmanı (controller + rotalar) **tamamen silindi** — yama/kilitleme değil, kaldırma.

## Gerekçe
Bağımsız grep ile doğrulandı: `web/`, `admin/`, iOS'un hiçbiri bu uçları çağırmıyordu; tek bilinen çağıran uykudaki `brand-panel/` prototipiydi (Temmuz'da dokunulmamış, güncel durumu zaten Needs Validation). Kullanılmayan bir kod yolunu güvenlik yamasıyla sertleştirmek yerine kaldırmak, gelecekte aynı sınıf açığın tekrar unutulmasını yapısal olarak engelliyor.

3D üretim motorunun kendisi (kuyruk, Tripo servisi, dönüştürücüler, düz yüzey üreticisi) **duruyor** — silinen yalnızca dışarıdan erişilebilen HTTP uç katmanı; yeni mağaza sitesi kendi uçlarından (`seller-products`, `admin`) aynı motoru çağırıyor.

## Değerlendirilen Alternatifler
- Uçları ADMIN'e kilitlemek + retry'ı CAS'lamak (yama) — bu ara adım olarak zaten yapılmıştı (commit `c22602a`), ama kullanılmayan kodun kalıcı sertleştirilmesi yerine kaldırılması tercih edildi.

## Sonuçlar (Consequences)
- Satıcının eski `POST /products` ucundan `status: PUBLISHED` göndererek 3D zorunluluğunu ve admin onayını atlaması artık mümkün değil (aynı Codex turunda ayrıca kapatıldı — bkz. kayıt notu).
- Eski `/3d-pipeline` ucunun hak sayacına bakmadan sınırsız ücretli Tripo üretimine izin verme riski ortadan kalktı.
- Regresyon testleriyle korunuyor; 22 suite / 129+ test yeşil (bkz. kayıt notu, `.superpowers/sdd/progress.md`).

## Riskler
- Kaldırma commit'i main'e merge edildi (`44a4497`, `1c316b1`); geri dönüş gerekirse Git geçmişinde duruyor.

## Kaynak Toplantı
Bu bir toplantı kararı değil — main'e birleştirme öncesi zorunlu Codex inceleme kapısının bulgusu üzerine kurucu kararı (2026-07-31). Kayıt: [[2026-07-31 Kategori 3D Stratejisi, Tripo Kredi Ölçümü, iOS Doku Düzeltmesi ve Main Merge]].
