---
type: source
date: 2026-07-21
status: processed
related: []
---

# 2026-07-21 PM Panel Tartışması (AI panel — kaynak notu)

> **Kaynak notu.** Vault'a bağlam yedirme sırasında, kurucunun isteğiyle iki "senior product manager" personası (AI) master bağlam üzerinden iki turlu yazılı tartışma yaptı; tarafsız bir moderatör sentezledi. **Buradaki her şey öneri ve analizdir — karar değildir.** Kararlar yalnızca ekip verirse [[Decision Index]]'e girer. Sorular [[Open Questions]]'a taşındı.
>
> Personalar: **PM-A** = kullanıcı & pazar odaklı; **PM-B** = teknik ürün & platform odaklı.

## PM-A — 1. Tur

# Livaro — Bağımsız Ürün Değerlendirmesi (1. Tur)

**Perspektif:** Senior Product Manager — kullanıcı değeri, pazar, ilk ürün kapsamı. Teknolojiye saygılı ama mesafeli.

## 1. Mevcut Durum Değerlendirmesi

**Güçlü yönler.** Beş haftada uçtan uca çalışan bir prototip çıkmış: oda tarama → texture'lı 3D oda → AI tasarım sahnesi → render galerisi + AR. Bu yürütme hızı ciddiye alınmalı. Daha da değerlisi, deney disiplini: Gaussian Splatting 4 günde kanıtla rafa kaldırılmış, ARKit mesh cihaz ısınması nedeniyle kapatılmış, generatif görüntü modelleri ölçü sadakati sağlayamadığı için bilinçli terk edilmiş — başarısızlıklar belgelenmiş. Erken ekiplerde nadir bir olgunluk. Ürün omurgası da doğru bir içgörüye oturuyor: "gerçek ölçü" (cm zorunluluğu, oda ölçüsünün sert filtre olması). Mobilyada "bu koltuk buraya sığar mı?" gerçek bir problem.

**Riskler.** Tabloyu tersinden okuyayım: sıfır dış kullanıcı, sıfır gerçek satıcı, katalogda 3 test ürünü. Beş haftalık eforun neredeyse tamamı teknoloji tarafına gitmiş; talep ve arz tarafında tek bir doğrulama verisi yok. Bu, klasik "çözüm önce, problem sonra" deseni. Pazaryeri iki taraflı bir iş — şu an iki taraf da boş. Tripo3D pipeline'ının "hazır" olması, satıcının onu kullanacağı anlamına gelmiyor; hiç denenmedi. Ticari model (checkout mu lead mi), ilk kullanıcılar, MVP kapsamı, satıcı onboarding'i: hepsi açık. Teknik yol netleşirken ürün yolu hiç netleşmemiş. Operasyonel olarak backend kurucunun Mac'inde ve TestFlight yok — yani dış kullanıcı testi fiziksel olarak imkânsız; bu tek başına tüm validasyonun blocker'ı. Akış 6 adıma uzamış (tarama + 4 köşe foto + 2 yakın çekim): motivasyonlu kurucu için sorun değil, sıradan kullanıcı için her adım funnel kaybı. Kalite kırılgan: iki sessiz texture regresyonu ve RoomPlan'in TV'yi pencere sanması, "etkileyici demo" ile "güvenilir ürün" arasındaki mesafeyi gösteriyor.

**Kör noktalar.** Hedef kullanıcı tanımı yok: kim, hangi anda (taşınma? tadilat? tek parça alım?), bugün bu problemi nasıl çözüyor — bilinmiyor. LiDAR'lı iPhone (Pro modeller) zorunluluğunun Türkiye pazarında kitleyi ne kadar daralttığı hiç ele alınmamış; rakam bilinmiyor ama asıl sorun, sorunun masada bile olmaması. Birim ekonomisi hesaplanmamış: Modal render (~2-3 dk/T4) ve Tripo3D kredileri kullanım başına maliyet üretiyor; gelir modeli belirsizken maliyet modeli de belirsiz. Rekabet/alternatif analizi vault'ta görünmüyor: kullanıcının bugünkü alternatifi karşısında konum tanımsız.

## 2. En Kritik 3 Varsayım ve Testleri

**V1 — Talep:** "Gerçek ölçülü 3D görselleştirme, mobilya alıcısı için 6 adımlık taramaya katlanacak kadar değerli ve çıktı kalitesi satın alma güveni yaratıyor." **Test:** TestFlight beklemeden, kurucu cihazıyla 8-10 hedef kullanıcıyla moderated test: akışı kendi evlerinde tamamlıyorlar mı, nerede bırakıyorlar, render'a bakıp "bu görsele güvenerek satın alır mıydın?" sorusuna ne diyorlar. Başarı ölçütü (tamamlama oranı + güven beyanı) testten önce yazılmalı.

**V2 — Arz:** "Satıcılar 4 fotoğraf + cm ölçüsüyle ürün yükler ve 3D çıktıyı markalarını temsil edecek kalitede bulur." **Test:** 3-5 gerçek mobilya satıcısına brand-panel'i kullandırt: kaç ürün yüklediler, Tripo3D çıktısını onayladılar mı, nerede takıldılar. Pipeline hazır; tek eksik satıcı bulup denemek.

**V3 — Pazar erişimi:** "LiDAR zorunluluğu hedef segmentte anlamlı bir kitle bırakıyor." **Test:** Hedef kullanıcı tanımı netleşince o segmentte cihaz sahipliğini ölç (ön kayıt landing sayfası + cihaz sorusu gibi ucuz bir yöntem); LiDAR'sız degrade akış gerekip gerekmediğine bu veriyle karar ver.

(Birim ekonomisi dördüncü sırada: test değil hesap gerektiriyor — bir haftalık masa başı iş, hemen yapılmalı.)

## 3. İlk Ürün Ne Olmalı — Pozisyonum

*(Öneri; karar değil.)* İlk ürün tam pazaryeri **olmamalı**. Önerim: **tek segment, dar katalog, lead-gen concierge MVP.**

- **Kapsam:** 1-2 anlaşmalı satıcı, 50-100 gerçek 3D'li ürün, tek şehir/tek segment. Checkout yok; "bu ürünü istiyorum" → satıcıya lead. Ödeme, lojistik, iade ertelenir — doğrulanmamış talebe altyapı kurulmaz.
- **Teknolojide feature freeze:** Bugünkü texture kalitesi "yeterli" ilan edilip dondurulur (regresyon testi eklenerek); kalan efor deployment + TestFlight + katalog doldurma + kullanıcı testine kayar. Backend'in Mac'ten çıkması ve TestFlight birinci önceliktir, çünkü bunlar olmadan hiçbir öğrenme mümkün değil.
- **Başarı tanımı öğrenme cinsinden:** 20-30 gerçek kullanıcı akışı tamamlasın; kaçı tasarım sahnesine ulaşıyor, kaçı lead bırakıyor, satıcı lead'lere ne diyor. Bu sayılar V1 ve V2'yi aynı anda test eder.
- **Gerekçe:** Ekibin kanıtlanmış gücü mühendislik; kanıtlanmamış olan her şey pazar tarafında. İlk ürün, en zayıf bilgiyi en ucuza üretecek şekilde tasarlanmalı — daha fazla teknoloji değil, pazarla ilk temas.

## 4. Kuruculara Sorular

1. **Hedef kullanıcı kim ve hangi anda devreye giriyoruz (taşınma, tadilat, tek parça alım)?** — Akış toleransı, kanal ve katalog kapsamı tamamen bu cevaba bağlı.
2. **18 ürün neden silindi ve gerçek katalog neden hiç doldurulmadı?** — Pratik bir engel mi, yoksa arz tarafındaki işten kaçınma sinyali mi, ayırt etmem gerekiyor.
3. **Bugüne kadar tek bir mobilya satıcısıyla konuşuldu mu; panele ürün yüklemeye istekli bir marka var mı?** — Pazaryerinin yarısı satıcı; sıfır temasla arz varsayımı tamamen boşta.
4. **Checkout mu lead mi sorusunda içgüdünüz ne ve hangi kanıt sizi ikna eder?** — Gelir modeli, birim ekonomisi ve MVP kapsamı bu karara zincirli.
5. **Render + Tripo3D için kullanım başına maliyet ne; kullanıcı/satıcı başına kaç render ve model öngörüyorsunuz?** — Birim ekonomisi hesaplanmadan "bedava demo" ile "sürdürülebilir ürün" ayrımı yapılamaz.
6. **TestFlight ve production deployment'ın önündeki somut engel ne, ne kadarlık iş?** — Dış kullanıcıya ulaşmanın tek yolu bu; her hafta gecikme, beş haftalık mühendisliğin doğrulanmamış kalması demek.

**Özet yargım:** Teknik risk büyük ölçüde alınmış ve akıllıca azaltılmış; ürün riski ise hiç alınmamış. Önümüzdeki 4-6 hafta daha fazla teknolojiye değil, ilk 30 kullanıcıya ve ilk 3 satıcıya harcanmalı.
---

## PM-B — 1. Tur

# Livaro — 1. Tur Bağımsız Değerlendirme (Persona B: Teknik Ürün / Platform Perspektifi)

## 1) Mevcut Durum Değerlendirmesi

**Güçlü yönler.** Beş haftada iki kurucunun çıkardığı iş, mühendislik yürütme kapasitesi açısından etkileyici: uçtan uca çalışan bir prototip var (RoomPlan tarama → texture'lı 3D oda → AI Designer → Blender render galerisi + USDZ). Daha önemlisi, ekibin **deney disiplini** sağlıklı: Gaussian Splatting 4 günde teşhisle (ARKit pozlarının 3DGS için yetersizliği COLMAP ile kanıtlanmış) rafa kaldırılmış; generatif render (gpt-image-1, ControlNet) "ölçü sadakati yok" diye bilinçli terk edilmiş. Bu "hızlı dene, kanıtla, bırak" döngüsü erken aşamada nadir görülür ve teknik yol seçiminde güven verir. Mimari seçimler de pragmatik: sıfır 3. parti iOS bağımlılığı, presigned R2, Modal'da izole GPU işi — hepsi düşük operasyonel yük hedefliyor. Gerçek cm ölçüsü zorunluluğu + "ölçü sadakati her şeyden önce gelir" ilkesi, generatif görsel araçlarının kolay kopyalayamayacağı potansiyel bir ayrışma ekseni.

**Riskler.** En büyüğü **sıralama (sequencing) hatası riski**: beş haftanın neredeyse tamamı pipeline'ın en zor ve en ayırt edici parçasına (3D/texture) gitmiş; ama pazaryerinin ön koşulu olan katalog 3 test üründe kalmış, hiç dış kullanıcı testi yok, deployment/TestFlight açık, ticari model belirsiz. Yani "teknoloji hangi ürün deneyimini mümkün kılıyor" sorusunun cevabı henüz hiçbir gerçek kullanıcıda doğrulanmadı. İkincisi, **pipeline kırılganlığı**: texture pipeline'da iki sessiz regresyon yaşanmış, RoomPlan TV'yi pencere sanabiliyor, Tripo GLB rotasyonu doğrulanmamış, Tripo retry'ları cache'siz kredi yakıyor. Bu, "demo'da çalışan" ile "yüz kullanıcıda çalışan" arasındaki farkın henüz kapanmadığını gösteriyor. Üçüncüsü, **birim ekonomisi bilinmiyor**: T4'te 2-3 dk/render'ın maliyeti hesaplanmamış; render başına maliyet ile (henüz tanımsız) gelir modeli arasındaki ilişki tamamen açık.

**Kör noktalar.** (a) **LiDAR zorunluluğu** pazarın yalnızca iPhone Pro dilimine hitap ettiği anlamına geliyor; bu kısıtın TAM'e etkisi vault'ta "ele alınmadı" olarak duruyor — kritik bir stratejik boşluk. (b) **Tarama akışı ~6 adıma** çıktı (tarama + 4 köşe foto + 2 yakın çekim); mühendislik gözüyle her adım kaliteyi artırıyor, ama kullanıcı gözüyle her adım bir terk noktası — bu gerilim hiç ölçülmedi. (c) **Arz tarafı** neredeyse hiç düşünülmemiş: brand-panel var ama gerçek bir satıcının 4 açı fotoğrafla ürün yükleyip Tripo çıktısını kabul edilebilir bulup bulmayacağı bilinmiyor. İki taraflı pazaryerinde arz kalitesi talep deneyiminin tavanıdır.

## 2) En Kritik 3 Varsayım ve Testleri

**V1 — "Fotoğraftan kırpılan texture'lı RoomPlan odası, kullanıcının 'bu benim odam' diyeceği kadar iyi."** Tüm aktif 3D yolu buna dayanıyor. Test: 10-15 dış kullanıcıya (TestFlight) kendi odalarını taratıp render'ı göster; "odanızı tanıdınız mı / bu görselle mobilya alır mıydınız" sorusuna yapılandırılmış cevap topla. Şu an sıfır dış veri var.

**V2 — "6 adımlı tarama+foto akışını sıradan kullanıcı tamamlar."** Kurucular tamamlıyor; bu hiçbir şey kanıtlamaz. Test: aynı TestFlight grubunda adım bazlı funnel ölçümü (hangi adımda kaç kişi bırakıyor, toplam süre). Terk %50'yi aşarsa akış kısaltılmalı, kalite pahasına bile.

**V3 — "Tripo3D pipeline'ı gerçek satıcı kataloğunu kabul edilebilir kalite ve maliyette 3D'ye çevirir."** Pazaryeri iddiasının tamamı buna bağlı; bugüne kadar yalnızca 3 test ürünle çalıştı. Test: tek bir gerçek satıcıdan 30-50 ürün al, uçtan uca işle; kalite kabul oranını, ürün başına krediyi/maliyeti ve rotasyon/ölçek hatalarını ölç. (Bunun ön koşulu: retry cache ve GLB rotasyon doğrulaması — yoksa test kendisi kredi yakar.)

## 3) İlk Ürün Pozisyonum (öneri, karar değil)

Pozisyonum: **ilk ürün "pazaryeri" değil, "odanı tara, ölçüyle doğru şekilde döşenmiş halini gör" deneyimi olmalı; satış, ilk sürümde ürün sayfasına/lead'e yönlendirme kadar ince tutulmalı.** Gerekçe teknik-ürün açısından net: (1) Ekibin gerçek moat adayı, ölçü-sadık tarama→render pipeline'ı; çift taraflı pazaryeri likiditesi ise bugün en zayıf halka (3 ürün, 0 satıcı, 0 kullanıcı). Moat'ı olan tarafı önce doğrulamak, olmayanı sonra inşa etmek doğru sıralamadır. (2) Checkout, ödeme, iade, satıcı operasyonu gibi pazaryeri maliyetlerini üstlenmeden önce, insanların bu görselleştirmeyi *isteyip istemediği* kanıtlanmalı. (3) Dar kapsam, kırılgan pipeline'ı sertleştirmeye alan açar: az akış, çok tekrar. Bunun MVP kapsamı bence: TestFlight'ta tarama→render→AI öneri + tek satıcıdan doldurulmuş 30-50 ürünlük gerçek katalog + ürün başı maliyet ölçümü. Doğrudan checkout, satıcı self-service onboarding ve LiDAR'sız cihaz desteği bilinçli olarak kapsam dışı. Bu bir öneridir; Open Questions'taki "ticari model" sorusunun cevabını vermez, sadece cevabı veri toplayarak aramayı önerir.

## 4) Kuruculara Sorular

1. **Render başına gerçek maliyet (Modal T4 + OpenAI + Tripo krediler dahil) nedir?** — Birim ekonomisi bilinmeden hangi ticari modelin ayakta kalacağı tartışılamaz.
2. **LiDAR'lı iPhone zorunluluğu bilinçli bir "premium segment" seçimi mi, geçici bir teknik kısıt mı?** — Cevap, hedef kullanıcı tanımını ve LiDAR'sız fallback'e (Open Questions'ta duran manuel/CV yaklaşımı) yatırım kararını doğrudan belirler.
3. **İlk gerçek satıcı kim olacak ve onunla konuşuldu mu?** — Katalog doldurma "öncelikli iş" olarak yazılmış ama arz tarafında tek bir doğrulanmış ilişki görünmüyor; pazaryeri iddiası bunsuz test edilemez.
4. **TestFlight'a çıkmayı bugüne kadar engelleyen şey nedir — teknik bir eksik mi, "henüz hazır değil" hissi mi?** — Beş haftalık yoğun iterasyona rağmen sıfır dış kullanıcı, en pahalı öğrenme döngüsünün hiç başlamadığı anlamına geliyor.
5. **Texture pipeline'daki iki sessiz regresyondan sonra otomatik doğrulama (golden-image testi, R2 çıktı kontrolü) planlanıyor mu?** — Kırılgan bir pipeline'ın üstüne kullanıcı trafiği bindirmek, ilk izlenimi tek seferde yakma riskidir.
6. **ARKit Scene Reconstruction "harika sonuç" verdiyse, ısınma/crash sorunu çözülebilir mi diye ne kadar bakıldı — yoksa kalıcı fizik kısıtı mı?** — Aktif yol (köşe foto + kırpma) 6 adımlık UX maliyeti ödüyor; kapatılan yol daha iyi UX'le benzer kaliteyi verebiliyorsa sequencing yeniden düşünülmeli.

**Bilinmeyenler dürüst kalsın:** kullanıcı talebi, satıcı ilgisi, birim maliyet, LiDAR penetrasyonunun etkisi — bunların hiçbirinde bugün veri yok; yukarıdaki testler tam da bu boşlukları kapatmak için.
---

## PM-A — 2. Tur (PM-B'ye cevap)

# 2. Tur — PM-B'ye Cevap (Persona A: kullanıcı & pazar)

## 1) Katıldığım noktalar

**Sequencing hatası teşhisi.** Aynı yerdeyiz: beş haftanın tamamı teknoloji riskine harcanmış, ürün riski hiç alınmamış. Bunu ikimizin de bağımsız olarak bir numaralı risk seçmesi, kuruculara verilecek en net sinyal olmalı.

**"Arz kalitesi talep deneyiminin tavanıdır."** Bu cümleye tamamen katılıyorum ve benim V2'mi (satıcı arzı varsayımı) güçlendiriyor. En iyi tarama deneyimi bile 3 test ürünlük katalogla değersiz; kullanıcının göreceği şey sonuçta üründür. Senin V3 tasarımın (tek satıcıdan 30-50 ürün, kalite kabul oranı + ürün başı maliyet) benim satıcı testimden daha somut ve ölçülebilir — bunu aynen alırım.

**Funnel ölçümü ve %50 terk eşiği.** V2'ne katılıyorum, özellikle "kalite pahasına bile kısaltılmalı" kısmına. Kullanıcı odaklı biri olarak ekleyeyim: terk verisi gelmeden akışın uzunluğu hakkında ikimiz de spekülasyon yapıyoruz; ölçüm bunu bitirir.

## 2) Katılmadığım / eksik bulduğum noktalar

**"İlk ürün pazaryeri değil, görselleştirme deneyimi" pozisyonun eksik.** MVP kapsamın (tarama→render + 30-50 gerçek ürün) benimkine yakın, ama başarı ölçütlerin tamamen teknik: kalite kabul oranı, ürün başı maliyet, pipeline sertleşmesi. Bunlar "yapabiliyor muyuz?" sorusunu cevaplar; "kimse ister mi?" sorusunu cevaplamaz. Bedava ve etkileyici bir 3D oda deneyimini herkes sever — bu vanity validation'dır. Satın alma niyetinin tek ucuz göstergesi somut bir ticari aksiyondur: lead bırakma. "Satış, ürün sayfasına yönlendirme kadar ince" deyip bunu ölçüt yapmazsan, MVP'nin sonunda elimizde yine sadece teknoloji kanıtı olur. Lead aksiyonu ve lead→satıcı dönüşümü MVP'nin birincil metriği olmalı; bu ek mühendislik değil, ölçüm tanımı meselesi.

**"Pipeline gerçek moat adayı" çerçevesi tehlikeli.** Doğrulanmamış bir talebin üzerine moat inşa edilmez. Pazaryerlerinde kalıcı moat teknoloji değil, arz likiditesi ve dağıtımdır; ölçü-sadık render bugün ayrıştırıcı olabilir ama Apple'ın veya bir başkasının bunu commoditize etmeyeceğini bilmiyoruz (bilinmiyor). Bu çerçeve, ekibi tam da çıkması gereken sarmalın içine — "pipeline'ı biraz daha sertleştirelim" — geri çeker.

**6. sorun (ARKit mesh'i yeniden açmak) riskli bir kapı aralıyor.** Deney kanıtla kapatılmış: cihaz ısınması ve crash. Funnel verisi elimizde yokken, UX maliyetini azaltmak için kapatılmış bir mühendislik yoluna geri dönmek, tam olarak eleştirdiğimiz sequencing hatasını tekrarlamak olur. Sıralama tersi olmalı: önce terk ölçülür; terk yüksekse önce ucuz çözümler denenir (yakın çekim adımları zaten isteğe bağlı — bunları varsayılan-kapalı yapmak sıfır maliyetli bir deney); ARKit ancak bunlar yetmezse masaya gelir.

**V1 testini TestFlight'a bağlaman gereksiz bir bağımlılık.** TestFlight açık bir blocker, evet — ama ilk öğrenmenin ön koşulu değil. Kurucu cihazıyla 8-10 kullanıcının evinde moderated test bu hafta yapılabilir. Deployment beklerken üç hafta daha sıfır kullanıcı verisiyle geçirmek kabul edilemez.

## 3) Pozisyonumda değişenler

İki güncelleme yapıyorum. (1) İlk turda "1-2 satıcı, 50-100 ürün" demiştim; senin "tek satıcı, 30-50 ürün" kapsamın daha yalın ve öğrenme için yeterli — ona geliyorum. (2) Satıcı pilotundan **önce** pipeline'a asgari güvenilirlik yatırımı (regresyon testi, retry cache, rotasyon doğrulaması) konusunda beni ikna ettin: pilot sırasında sessiz bir regresyon, ilk ve tek satıcı ilişkisini yakar. Bunu "feature freeze" tanımıma istisna olarak ekliyorum. Değişmeyen: lead aksiyonu MVP'de kalmalı ve birincil metrik olmalı.

## 4) İkimizin de gözden kaçırdığı konu

**İlk kullanıcılar bu ürünü nereden bulacak?** İkimiz de "20-30 kullanıcı", "10-15 TestFlight kullanıcısı" dedik ama edinme kanalı hakkında tek kelime etmedik. LiDAR'lı iPhone'u olan, Türkçe konuşan, mobilya alma anındaki kullanıcıya hangi kanaldan ulaşılacak — bilinmiyor ve vault'ta hiç ele alınmamış görünüyor. MVP tanımına "ilk 30 kullanıcının kaynağı" açıkça yazılmalı; kanal hipotezi olmayan MVP, testi yapılamayan hipotezdir. İkinci kısa not: kullanıcılar evlerinin içini tarayıp fotoğraflıyor — bu hassas kişisel veri; KVKK/consent/saklama konusu ikimizin de listesinde yoktu ve güven, dönüşümü doğrudan etkiler.

**Ortak zemin önerisi:** Teşhiste zaten hemfikiriz. Sentez şu olabilir: senin MVP kapsamın + benim ticari ölçütüm (lead), senin pipeline ön koşulların + benim "TestFlight'ı bekleme, bu hafta moderated test" takvimim.
---

## PM-B — 2. Tur (PM-A'ya cevap)

# 2. Tur — PM-A'ya Cevap (Persona B: Teknik Ürün / Platform Perspektifi)

## 1) Katıldığım Noktalar

**"Teknik risk akıllıca alınmış; ürün riski hiç alınmamış" özet yargısına tamamen katılıyorum.** Bu, benim "sequencing hatası" tespitimin daha keskin ifadesi. Beş haftalık efor dağılımı bunu doğruluyor: üç farklı 3D yaklaşımı denenip kanıtla elenirken, tek bir dış kullanıcı ya da satıcı görüşmesi yapılmamış.

**Backend'in Mac'ten çıkması + TestFlight'ın "birinci öncelik" ilan edilmesine katılıyorum ve kendi listemde eksik sıraladığımı kabul ediyorum.** Ben bunu kuruculara soru olarak bırakmıştım; PM-A haklı — bu bir soru değil, tüm validasyonun fiziksel ön koşulu. mDNS'li dev backend'le hiçbir dış test koşulamaz; benim önerdiğim V1/V2 testleri de dahil.

**"Kurucu cihazıyla moderated test" fikri benim test tasarımımdan daha iyi.** Ben TestFlight'ı beklemeyi varsaymıştım; PM-A'nın 8-10 kişilik moderated yaklaşımı, deployment işi bitmeden talep sinyali toplamaya başlar. İki haftalık öğrenme kazancı bedava.

## 2) Karşı Çıktığım / Eksik Bulduğum Noktalar

**"Bugünkü texture kalitesi 'yeterli' ilan edilip dondurulur" — buna teknik zeminde itiraz ediyorum.** Kaliteyi fiat'la "yeterli" ilan edemeyiz; yeterlilik eşiğini tanımlayacak tek merci, PM-A'nın kendi önerdiği moderated testlerdir. Daha önemlisi: iki sessiz regresyon yaşamış, TV'yi pencere sanabilen, mobilya min-oran fit'i ölçek algısını bozabilen bir pipeline'ı bugünkü haliyle dondurmak, "ilk 30 kullanıcının bir kısmına bozuk oda göstermeyi" dondurmak demek. Doğru formül: **kapsam dondurulur, kalite dondurulmaz** — yeni özellik yok, ama golden-image regresyon testi + R2 çıktı doğrulaması + bilinen veri hatalarına (TV=pencere) düzeltme/uyarı katmanı freeze'in parçası olmalı. Bu 1-2 haftalık sertleştirme, kullanıcı testinin ölçtüğü şeyin "pipeline'ın şanslı günü" değil gerçek kalite olmasını sağlar.

**"50-100 ürünlük katalog" hedefi, pipeline hazırlığı kanıtlanmadan riskli.** Tripo retry'ları cache'siz kredi yakıyor ve GLB rotasyon işareti hiç doğrulanmadı. 100 ürünü bugünkü pipeline'dan geçirmek, maliyeti ölçülmemiş bir işi ölçeklemek olur; rotasyon hatalıysa 100 bozuk model üretiriz. Önerim kademeli: önce retry cache + rotasyon doğrulaması (küçük iş), sonra 30-50 ürünlük kontrollü parti ile **kalite kabul oranı ve ürün başı maliyet ölçümü**, sonra 100'e çıkış. Ayrıca PM-A'nın "18 ürün neden silindi" sorusunun cevabı vault'ta zaten var: usdz'siz oldukları için 15 Temmuz'da bilinçli silindiler (`Marketplace Model`, oturum import'u). Gerçek soru "neden silindi" değil, **"neden hiç yeniden doldurulmadı"** — kuruculara bunu sormalıyız.

**LiDAR testi olarak "ön kayıt landing + cihaz sorusu" zayıf sinyal.** Landing, vaade olan merakı ölçer; 6 adımlık taramaya katlanma niyetini ve cihaz kısıtının gerçek etkisini ölçmez (self-report cihaz verisi de gürültülüdür). LiDAR sorusu bence bir pazarlama testi değil, **strateji + mühendislik kararı**: ya bilinçli "Pro segment" seçimi yazılır, ya da Open Questions'ta zaten duran LiDAR'sız fallback yoluna (manuel/CV) yatırım planlanır. Landing'i ancak mesaj testi olarak, bu kararın yerine geçmeden koşarım.

## 3) Pozisyonumda Değişenler

İki güncelleme: (a) TestFlight/deployment'ı soru listemden çıkarıp **1 numaralı ön koşul** yapıyorum. (b) Test sıralamamı değiştiriyorum: moderated test önce, TestFlight kohortu sonra. İlk ürün pozisyonum ise değişmedi, güçlendi — PM-A'nın "concierge lead-gen MVP"si ile benim "tarama→görselleştirme deneyimi + ince lead katmanı" önerim fiilen aynı ürün; iki bağımsız perspektifin aynı yere çıkması, checkout'lu tam pazaryerinin masadan kalkması gerektiğine dair güçlü bir işaret.

## 4) İkimizin de Gözden Kaçırdığı Konu

**Ev içi görüntü verisinin gizliliği ve işleme zinciri.** Bu üründe kullanıcı, evinin içini tarayıp fotoğraflıyor; bu görüntüler R2'de saklanıyor ve texture/bbox analizi için OpenAI'ye (GPT-4o) gidiyor. Ne ben ne PM-A bunu andık. Türkiye pazarında KVKK açısından açık rıza, saklama süresi ve 3. parti işleyici (OpenAI, Modal, Replicate — hepsi yurt dışı) aktarımı konuşulmamış görünüyor; vault'ta da bir iz yok (bilinmiyor). Dış kullanıcı testine çıkmadan önce asgari bir rıza metni ve veri saklama politikası şart — bu, hem hukuki hem güven (satın alma güveni tam da PM-A'nın V1'i) meselesi. İkinci küçük ekleme: 2-3 dakikalık async render'ın **başarısızlık anındaki kullanıcı deneyimi** (5 sn polling'de hata olursa kullanıcı ne görüyor?) tanımsız; ilk dış testte bu boşluk kendini gösterecektir.
---

## Moderatör Sentezi

### Fikir Birliği Noktaları
1. **Sequencing hatası — bir numaralı tespit.** Beş haftanın tamamı teknoloji riskine harcandı, ürün riski hiç alınmadı (0 dış kullanıcı, 0 satıcı, 3 test ürünü). İki PM buna bağımsız olarak vardı.
2. **İlk ürün tam pazaryeri olmamalı.** PM-A'nın "concierge lead-gen MVP"si ile PM-B'nin "tarama→görselleştirme + ince lead katmanı" önerisi fiilen aynı ürün. Checkout'lu tam pazaryeri iki bağımsız perspektifte de masadan kalktı (öneri).
3. **Deployment + TestFlight = validasyonun fiziksel ön koşulu; ama ilk öğrenme beklemez.** PM-B, PM-A'nın "bu hafta kurucu cihazıyla 8-10 kullanıcıyla moderated test" yaklaşımını benimsedi.
4. **Katalog pilotu: tek satıcıdan 30-50 gerçek ürün** + kalite kabul oranı + ürün başı maliyet ölçümü (PM-B tasarımı; PM-A açıkça bu kapsama geldi).
5. **Pilot öncesi asgari pipeline güvenilirlik yatırımı**: golden-image/regresyon testi, Tripo retry cache, GLB rotasyon doğrulaması (PM-A bunu feature-freeze tanımına istisna olarak kabul etti).
6. **Birim ekonomisi hesabı hemen yapılmalı** (masa başı iş; render + Tripo + OpenAI kullanım başına maliyet).
7. **Deney disiplini övgüsü**: "hızlı dene, kanıtla, bırak" kültürü (gsplat/ARKit mesh/generatif render) korunmalı — ama artık ürün hipotezlerine uygulanmalı.
8. **Ortak kör nokta (ikisi de sonradan yakaladı):** (a) **edinme kanalı** — ilk 30 kullanıcının nereden geleceği hiç konuşulmadı; (b) **KVKK/gizlilik** — ev içi tarama+fotoğraflar yurt dışı işleyicilere (OpenAI, Modal, Replicate) gidiyor; rıza metni, saklama süresi, aydınlatma yok (bilinmiyor). Dış teste çıkmadan asgari rıza + saklama politikası şart.

### Süren Fikir Ayrılıkları
| Konu | PM-A | PM-B | Moderatör notu |
|---|---|---|---|
| Kalite dondurulsun mu? | Bugünkü kalite "yeterli" ilan edilip feature freeze | **Kapsam donar, kalite donmaz** — sertleştirme freeze'in parçası | Fark daraldı; kalan soru "yeterlilik eşiğini kim belirler" — cevabı moderated test verir |
| MVP birincil metriği | **Lead aksiyonu** (ticari sinyal) — yoksa "vanity validation" | Kalite kabul oranı + ürün başı maliyet (teknik hazırlık) | İkisi farklı soruları ölçer; MVP'de ikisi de olmalı ama "başarı" tanımı ticari sinyalsiz olamaz — PM-A'nın itirazı güçlü |
| "Pipeline = moat" çerçevesi | Tehlikeli: moat arz likiditesi + dağıtımdır; doğrulanmamış talebe moat inşa edilmez | Ölçü-sadık pipeline gerçek moat adayı | Talep kanıtı gelene dek PM-A çerçevesi güvenli varsayılan; kanıt gelirse PM-B çerçevesi yatırımı meşrulaştırır |
| ARKit mesh yeniden açılsın mı? | Funnel verisi olmadan açmak sequencing hatasının tekrarı; önce ucuz çözüm (yakın çekimleri varsayılan-kapalı yap) | Soru açık kalmalı: 6 adımlık UX maliyeti vs kapatılmış-daha-iyi-UX yolu | Sıra net: önce funnel ölçümü; terk yüksekse önce ucuz deneyler; ARKit en son |
| LiDAR kısıtı nasıl test edilir? | Ön kayıt landing + cihaz sorusu (ucuz sinyal) | Landing zayıf sinyal; bu bir strateji+mühendislik kararı (premium segment mi, fallback yatırımı mı) | Karar kurucularda (segment seçimi); landing yalnızca mesaj testi olarak koşulmalı |

### Riskler ve Doğrulanmamış Varsayımlar (öncelik sırasıyla)
1. **Talep**: "gerçek ölçülü 3D, 6 adımlık taramaya değer + satın alma güveni yaratır" — sıfır veri.
2. **Funnel**: sıradan kullanıcı akışı tamamlar mı (terk eşiği %50 önerildi) — sıfır veri.
3. **Arz**: satıcı 4 foto + cm ile yükler, Tripo çıktısını markasına yakıştırır mı — sıfır veri; ayrıca Tripo kalite/maliyet ölçülmedi.
4. **Edinme kanalı** tanımsız; kanal hipotezi olmayan MVP test edilemez.
5. **KVKK/gizlilik** ele alınmadı; güven, dönüşümü doğrudan etkiler.
6. **Birim ekonomisi** hesaplanmadı.
7. **Pipeline kırılganlığı**: iki sessiz regresyon, TV=pencere, rotasyon doğrulanmamış; ayrıca 2-3 dk async render'ın hata anındaki UX'i tanımsız.

### Kuruculara Öneriler (öneri — karar değil)
1. **Bu hafta**: kurucu cihazıyla 8-10 hedef kullanıcıyla moderated test (başarı ölçütü önceden yazılı) + birim ekonomisi hesabı + asgari KVKK rıza metni.
2. **Paralel (1-2 hafta)**: Tripo retry cache + GLB rotasyon doğrulaması + golden-image regresyon testi; sonra tek satıcıdan 30-50 ürünlük kontrollü katalog pilotu.
3. **Ardından**: backend'in Mac'ten çıkması + TestFlight (tüm dış validasyonun ön koşulu).
4. **MVP tanımına yazılsın**: lead aksiyonu birincil ticari metrik + "ilk 30 kullanıcının kanalı" açıkça belirtilmiş olmalı.
5. **Feature freeze kapsamda** (yeni özellik yok); kalite sertleştirme serbest.
6. Yakın çekim adımlarını funnel ölçümünde **varsayılan-kapalı** varyantla A/B'lemek sıfır maliyetli ilk deney.

> Sorular [[Open Questions]]'a işlendi. Bu panel çıktısı üzerinden verilen her gerçek ekip kararı ayrı karar notu olmalı.

---

## Kurucu Yanıtları (2026-07-21, Selim)

Panelin dört öncelikli sorusuna kurucu yanıtları:
1. **İlk ürün kapsamı (görselleştirme + lead MVP önerisi):** "Henüz karar yok" — bilinçli erteleme; test verisi görülmeden karar verilmeyecek. Soru [[Open Questions]]'ta açık kalır.
2. **Hedef kullanıcı anı (taşınma/tadilat/tek parça):** "Henüz net değil" — açık.
3. **İlk satıcı:** "**Aday var, görüşülmedi**" — akılda satıcı adayı/adayları var, henüz temas kurulmadı. (Yeni bilgi; [[Seller Experience]]'a işlendi.)
4. **LiDAR zorunluluğu:** "Henüz düşünülmedi" — açık.

### Güncelleme (aynı gün, sonra)
Kurucu 1. sorudaki pozisyonunu güncelledi: **"Şimdilik bu öneriyi benimse — ama ileride sepet ve checkout da gelecek."** → Karar notu açıldı: [[2026-07-21 İlk ürün kapsamı görselleştirme + lead]].

### Güncelleme (aynı gün, hedef kullanıcı anı sorusu)
Kurucu PM-A'nın 1 numaralı sorusunu (hedef kullanıcı hangi anda devreye giriyor) yanıtladı: **"İlk sürümümüzde taşınma anı ve tadilat/yenileme üzerine kuralım. İleriki sürümümüzde tek parça alımla ilgili kullanıcılara da yöneleceğiz."** → Karar notu açıldı: [[2026-07-21 Hedef kullanıcı anı — taşınma ve tadilat]].
