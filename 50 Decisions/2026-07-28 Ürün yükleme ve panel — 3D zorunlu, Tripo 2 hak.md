---
type: decision
status: accepted
created: 2026-07-28
source: "[[2026 07 28 Thinking Session — Mağaza Web Paneli User Journey]]"
related: ["[[Seller Experience]]", "[[2026-07-24 Pilot marka kriterleri]]"]
---

# Ürün yükleme ve panel — 3D zorunlu, Tripo 2 hak

## Bağlam
Kurucunun taslak journey'sinde ürün formunda fiyat/ölçü/stok unutulmuştu (mevcut brand-panel prototipinde zorunlular); Tripo3D denemeleri cache'lenmediği için her deneme gerçek kredi harcıyor; 3D'nin zorunlu olup olmayacağı PM'lerin en büyük tartışmasıydı.

## Karar
- **Ürün formu:** ad, kategori, kategoriye özel sorular (ör. mobilya: sünger tipi, malzeme; halı: iplik, dokuma sıklığı, hav — soru setleri ayrı session'da hazırlanacak), **fiyat, ölçüler (en/boy/yükseklik), stoklu kategorilerde stok adedi**; en sonda fotoğraflar.
- Fotoğraf adımında **örnekli çekim rehberi** (4 açı, sade arka plan vb.).
- Tripo3D arka planda 3D üretir; mağaza modeli **web'de döndürerek inceler** → her ürün için **Onayla / Reddet**.
- **Tripo sınırı:** ürün başına **2 deneme hakkı**; **aynı fotoğraflarla ikinci üretim engellenir**; 2 hak da başarısızsa ürün **admin kuyruğuna "takıldı" olarak düşer** (pilotta kurucular fotoğrafları elle düzeltip yeniden dener).
- **3D zorunlu:** fotoğraf-only "3D hazırlanıyor" etiketiyle yayın **yok**; 3D'siz ürün **katalogda kayıtlı ama yayında değil**.
- Mağaza 3D onayından sonra ürün **admin onayından da geçer**, sonra yayınlanır.
- **Excel toplu yükleme de olacak** (tekil ekleme/düzeltme web formundan; [[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu|24 Tem]] Excel şablonu kararıyla uyumlu).
- **Ürün düzenleme/silme + "stokta yok" işaretleme** olacak.
- **Panel ana ekranı:** ilk günden boş metrikler yerine **ürün durumu** (yüklendi / 3D bekliyor / yayında); görüntülenme vb. metrikler veri birikince (vizyon metrikleri: [[Seller Experience]]).

## Gerekçe
3D'siz ürün müşteri uygulamasındaki AI tasarım/yerleştirme akışında kullanılamıyor — fotoğraf-only ürün ana vaadi sulandırır (PM tartışmasının vardığı nokta; kurucu onayı). 2-hak sınırı + aynı-fotoğraf engeli Tripo kredi israfını keser; admin kuyruğu "çıkmaz sokak" riskini kapatır.

## Değerlendirilen Alternatifler
- Fotoğraf + "3D hazırlanıyor" etiketiyle yayın (PM önerisi, pilot esnekliği) — reddedildi.
- 3 deneme hakkı — reddedildi, 2 seçildi.

## Riskler
- Tripo gerçek mobilya çeşitliliğinde test edilmedi; katı 3D kapısı pilotta katalog doldurmayı yavaşlatabilir (PM B uyarısı).
- Tripo aylık bütçesi tanımsız → [[Open Questions]].

## Kaynak Toplantı
[[2026 07 28 Thinking Session — Mağaza Web Paneli User Journey]] (PM tartışması: [[2026-07-28 PM Tartışması — Mağaza Paneli Journey]])
