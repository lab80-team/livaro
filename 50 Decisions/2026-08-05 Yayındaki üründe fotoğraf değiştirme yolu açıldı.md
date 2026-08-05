---
type: decision
status: accepted
created: 2026-08-05
source: "[[2026-08-05 Build Oturumu — Admin Paneli Dilim 1]]"
related: ["[[Admin Panel]]", "[[2026-08-04 Ürün düzenlemede yeniden onay — yalnız vitrin alanları]]", "[[Seller Experience]]"]
---

# Yayındaki üründe fotoğraf değiştirme yolu açıldı

## Bağlam

4 Ağustos kararı, yayındaki üründe **fotoğraf** değişikliğinin onay kuyruğuna düşmesini söylüyordu. İnşadan önceki kod doğrulaması şunu ortaya çıkardı: **yayındaki bir ürünün fotoğrafı bugün hiçbir yoldan değiştirilemiyor.**

Bu kasıtlı bir kilitti — fotoğraf değiştirme yalnız "taslak" ve "reddedilmiş" ürünlerde açıktı, çünkü 3D üretimi fotoğraf setine bağlı ve üretim sürerken seti değiştirmek akışı bozuyor.

Yani karar, kapalı olan bir kapının açılmasını gerektiriyordu. Kurucuya risk anlatılarak soruldu.

## Karar

**Yol açıldı** — ama mevcut kapı gevşetilerek değil, **ayrı bir uç eklenerek**.

Yeni uç yalnız yayındaki üründe çalışır ve:
- Ürünün kendisine **dokunmaz**
- 3D model kaydına **dokunmaz**
- Tripo deneme hakkı sayacına **dokunmaz** ve ona **bakmaz** (hiçbir 3D üretimi tetiklemediği için)

Fotoğraflar bekleyen düzenleme kaydına yazılır; ürün yayında kalır ve müşteri onaylı eski fotoğrafları görmeye devam eder.

## Gerekçe

Kurucu tercihi: 4 Ağustos kararı bunu gerektiriyor.

"Ayrı uç" biçimi, mevcut kilidin gerekçesini korumak için seçildi: o kilit 3D üretimini fotoğraf setiyle tutarlı tutuyor ve gevşetilseydi üretim sürerken set değiştirilebilirdi.

## Değerlendirilen Alternatifler

- **Şimdilik yalnız başlık + açıklama onaya düşsün, fotoğraf yolu kapalı kalsın** (mağaza ürünü yayından çekip düzeltir) — kurucuya sunuldu, seçilmedi.
- **Fotoğraf kısmını tamamen iptal et** — sunuldu, seçilmedi.

## Sonuçlar (Consequences)

- Mağaza panelinde yayındaki ürün için ayrı bir "Fotoğrafları Onaya Gönder" bölümü var; Tripo hak sayacı orada **hiç kullanılmıyor**. (Öncesinde yayındaki hakkı dolmuş üründe panel "3D deneme hakkınız doldu" gibi **yanlış** bir mesaj gösteriyordu — bu da düzeldi.)
- Kararın kapsamı iki katına çıkardığı kurucuya inşadan önce söylendi.
- Onaylanan yeni fotoğrafla mevcut 3D model arasında uyuşmazlık kalabilir → [[2026-08-05 3D yenileme dilim 1'den çıkarıldı — veri kaybı riski]].

## Riskler

- Fotoğraf değişimi sık olursa onay yükü artar — pilotta gözlenecek (4 Ağustos kararının aynı riski).
- Foto-3D uyuşmazlığı açık kalıyor (yukarıdaki karar notu).

## İlgili Bilgi

[[Admin Panel]], [[Seller Experience]]

## Kaynak

[[2026-08-05 Build Oturumu — Admin Paneli Dilim 1]]
