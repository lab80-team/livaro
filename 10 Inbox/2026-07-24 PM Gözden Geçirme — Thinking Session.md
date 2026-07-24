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

---

# 2. Tur — Teyit Turu Kararlarının İncelemesi (aynı gün)

> Kurucular 1. tur uyarılarını okuyup nihai kararlarını verdi (bazılarını kabul, bazılarını bilerek ret). 2 kıdemli PM merceği (iş/operasyon + ürün/teknik) nihai karar setini inceledi. **Öneridir, karar değildir.**

## Genel değerlendirme
Karar seti öncekinden belirgin şekilde daha sağlıklı: en büyük iki hukuki mayın (emanet, iade) doğru yöne çekildi; kapsam bazı yerlerde akıllıca budandı (sepet pasif, alternatif ertelendi). Asıl gerilim: en büyük iki bilinmeyen (AI yerleşim kalitesi, birim maliyet) bilinçli olarak sona ertelenirken kapsam geniş tutuldu (dolu oda boşaltma + AR) — risk sona yığılıyor; ucuz erken sinyallerle yönetilebilir.

## İyi bulunanlar
- Emanet lisanslı kuruluşa, iade/iptal yasaya — iki büyük yasal risk masadan kalktı.
- Anlık 3D + arka planda render + tek ürün değişiminin render tetiklememesi: hem hız hem masraf açısından doğru mimari.
- Kapsam disiplini: sepet pasif liste, alternatifle değiştirme ertelendi, checkout sonra.

## Kalan riskler ve önerilen emniyet kemerleri
1. **Maliyet freni yok** (sınırsız tasarım + bilinmeyen birim maliyet): servis sağlayıcılarda aylık harcama tavanı + uyarı; her tasarımın yaklaşık maliyetini ilk günden kaydet; sunucudan açılabilir gizli "limit anahtarı" hazırla; bot/kötüye kullanım için cihaz başına görünmez hız koruması.
2. **Dolu oda boşaltma + AR birlikte MVP'de** (en ağır teknik yük): içeride sıralı ilerle — önce boş oda akışını sağlamlaştır; dolu oda/AR için tarihli iç kontrol noktası + kalite çıtası (ör. 10 odadan 7 kabul); tutmazsa lansmanı bloklamak yerine "deneysel" etiketiyle aç.
3. **GPT-4o testi sona kaldı**: karar bozulmadan iki ucuz önlem — "iyi yerleşim" geçer/kalır ölçütünü ŞİMDİ yaz; eldeki 2-3 taramayla 1 günlük elle ön deneme yap (erken sinyal).
4. **İade akışı boş**: ilk satıştan önce tek sayfa — iade kargosunu kim öder, hangi ürünler cayma dışı, para kaç günde döner, emanet satıcıya hangi anda geçer; bir kerelik e-ticaret hukuku danışmanlığı.
5. **Hizmet bedeli kuralsız**: bedelin iade koşulları, mağaza gecikirse ne olacağı, tahsilat yolu (sağlayıcı seçilmeden teknik olarak boşlukta) — ücret almadan önce tek sayfalık kural seti.

## Yeni endişeler
- Arka planda render + bildirim, her an açık sunucu gerektirir → **buluta taşınma öne çekilmeli** (Mac kapalıyken bildirim çalışmaz); "olabildiğince kullanıcı çek" hedefi de aynı ön şarta bağlı.
- Render sürerken kullanıcı ürün değiştirirse bildirimle gelen görsel eski tasarımı gösterir → basit sürüm/etiket kuralı gerek.
- %20 bütçe aşımı kullanıcıya sorulmadan uygulanırsa "bütçemi deldi" hissi → aşan ürünlere "bütçenin %X üstünde" rozeti + isteğe bağlı gösterim.

## İşlenme (2. tur)
- Açık kalan noktalar [[Open Questions]]'ta "PM 2. tur incelemesinin açık bıraktıkları" bölümünde.
