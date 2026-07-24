---
type: import
date: 2026-07-24
status: processed
related: ["[[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu]]"]
---

# PM Gözden Geçirme — Thinking Session (2026-07-24)

> Kurucuların isteğiyle, thinking session cevapları üzerine 3 kıdemli PM merceğiyle (pazaryeri/operasyon, ürün/MVP, teknik/maliyet) yapılan inceleme. **Bunlar öneridir, karar değildir** — karar ancak kurucular açıkça verirse [[Decision Index]]'e girer.

## Güçlü bulunanlar (ortak)
- Uçtan uca çalışan prototip (tarama → AI tasarım → render → AR) — "çoğu ekip anlatırken siz gösterebiliyorsunuz".
- Kapsam daraltma içgüdüsü doğru: checkout'suz sepet, misafir gezinme, chat yerine mevcut wizard, sıfırdan tasarım, hedef anın taşınma/tadilatla örtüşmesi.
- Pilot marka kriteri akıllıca: internette satan, fotoğrafı hazır, çeşitliliği yüksek firmalar.

## En büyük riskler
1. **Emanet para = lisans sorunu.** Parayı Livaro hesabında emanet tutmak Türkiye'de (6493 sayılı kanun) lisanslı ödeme kuruluşu işi; pazaryerleri bunu lisanslı sağlayıcının (ör. iyzico Pazaryeri, PayTR, Craftgate) aracı hesabıyla çözer. Öneri: sağlayıcıyı "sonra" değil şimdi seç; emanet/ödeme planlarını onun kuralları üstüne kur.
2. **"İptal yok" kuralı 14 gün cayma hakkıyla çelişiyor.** Mesafeli satışta standart üründe 14 gün gerekçesiz cayma yasal hak, mağaza onayına bağlanamaz; özel üretim istisnası ancak sipariş öncesi açık bilgilendirmeyle kurulur. Öneri: kargodan önce iptale de izin ver (iadeden çok daha ucuz); e-ticaret avukatından pilot paketi al (mesafeli satış metni + cayma + KVKK + pilot mağaza sözleşmesi).
3. **Ürünün kalbi (AI yerleşim) henüz ölçülmedi.** Öneri: 10-30 gerçek oda × tarz testi, basit geçti/kaldı listesi (kapı önü boş mu, çakışma var mı, bütçe/tarz tutuyor mu); GPT-4o mu kural tabanlı mı kararını bu puana bağla; ölçmeden pazaryeri özelliği büyütme.
4. **Birim maliyet bilinmeden ücretsiz + limitsiz model.** Her tasarım gerçek para (GPT-4o + 2-3 dk GPU + Replicate; Tripo retry'ları cache'siz). Öneri: bu hafta gerçek faturalardan maliyet tablosu (1 tarama / 1 tasarım / 1 ürün 3D'si kaç TL); kişi başı sayaç ilk sürümde; aylık harcama alarmı.
5. **Kapsam-kaynak uçurumu.** Anlatılan MVP (tarama+tasarım+AR+pazaryeri+emanet+teslimat+itiraz) 2 kişilik ekibin 6 ayına sığmaz. Öneri: MVP cümlesi — "Boş odanı tara, bütçe+tarzını söyle, gerçek ürünlerle döşenmiş odanı 3D gör, beğendiğin ürün için mağazaya talep bırak"; bu cümleye hizmet etmeyen her şey MVP dışı. İlk 10-20 siparişi tamamen elle yürüt.
6. **Web sitesi fotoğrafı ≠ Tripo3D'nin 4 açı formatı.** Toplu yüklemeden önce 20 ürünlük gerçek deneme (kalite kabul oranı + ürün başı maliyet + elle düzeltme süresi); katalog yayınına insan onay adımı; Tripo sonuçlarını sakla (retry bedavaya dönsün).
7. **Backend Mac'te + TestFlight yok.** Çevre pilotu bile fiilen başlayamaz; mağaza görüşmesinden önce bulut + TestFlight + KVKK onay ekranı.

## Kurucu kararlarına itirazlar (PM görüşleri — karar kurucularda)
| Konu | Kurucu kararı | PM görüşü |
|---|---|---|
| Emanet | Para Livaro'da emanet | Lisanslı sağlayıcının aracı hesabında tutulmalı; kendin kurma, hazırını kirala |
| İptal | Sipariş iptali yok | Yasal olarak savunulamaz; kargo öncesi iptal ayrıca senin de lehine |
| Oda boşaltma | Dolu odayı AI boşaltır | En zor görsel problem; hedef kitlenin odası zaten boş(altılabilir) — MVP'de "boş odanı tara" de |
| AR | Tüm oda AR'ı MVP'de | Dolu odada sanal mobilya gerçeğin üstüne biner; 3D+2D yeterli, AR'ı sonraya at veya tek ürüne indir |
| Yeniden tasarla 2 hak | 2 defa | Maliyet ölçülmeden konmuş limit; pilotta gevşek tut (ör. 10), veriyle belirle |
| Hizmet bedelli indirim | Baştan tahsil | Sıfır güvenle peşin ücret satılmaz + elle pazarlık ölçeklenmez; MVP'den tamamen çıkar |
| Reklamın tasarıma gömülmesi | AI reklamlı ürünü öne çıkarır | Tasarımın tarafsızlığı en değerli güven varlığı; sponsorlu ürün Keşfet/aramada kalmalı, tasarım sonucunda olmamalı |
| Gecikme cezası | 2 gecikmede bakiyeden kesinti | Gönüllü pilot firmadan para kesmek arzı kaçırır; pilotta puan/sıralama yeterli |
| Limitler | İleride | Sayaç 1 günlük iş; ilk sürümde olmalı |

## Somut MVP önerileri (özet)
- Ödeme sağyacısını bu ay seç (alt üye işyeri kaydı haftalar sürüyor); ödeme planlarını sipariş başına pazarlığa bırakma — 2 standart şablon (stoklu: tam ödeme+teslimle serbest bırakma / özel üretim: %X avans+teslimde kalan).
- Anlık deneyim kararı (kurucuların 8 ve 15. sorusunun cevabı): canlı 3D sahne ana sonuç ekranı — ürün değişimi/çıkarma anında orada; Blender render arka planda "fotoğrafın hazır" bildirimiyle; tek ürün değişimi asla tam render tetiklemesin.
- Teslim tutanağı + 48 saat itiraz penceresi + kanıta göre serbest bırakma kuralını pilot sözleşmesine yaz.
- Excel şablonunda gerçek ölçüler (en/boy/yükseklik) zorunlu alan; pilot ürünlerde elle doğrula (Tripo görsel üretir, ölçü garantisi vermez).
- LiDAR hunisi için ucuz yedek: elle ölçü girişi (video araştırmasından önce, birkaç günlük iş).

## İşlenme
- Riskler ve öneriler [[Open Questions]]'a soru olarak yansıtıldı; hiçbiri karar olarak kaydedilmedi.
- İlgili: [[2026 07 24 Thinking Session — Uçtan Uca Ürün Vizyonu]], [[2026-07-21 PM Panel Tartışması]]
