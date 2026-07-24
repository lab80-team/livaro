---
type: decision
status: accepted
created: 2026-07-21
source: "[[2026-07-21 PM Panel Tartışması]]"
related: []
---

# İlk ürün kapsamı: tarama→görselleştirme + ince lead katmanı (checkout sonra)

> **Güncelleme (2026-07-24)**: [[2026-07-24 Sepet MVP'de, checkout ödeme teknolojisi seçilince]] bu kararı güncelledi — sepete ekleme MVP'ye alındı; checkout ödeme teknolojisi seçilince entegre edilecek. "İnce lead katmanı"nın akıbeti (checkout öncesi sepetin davranışı) **To Be Decided** → [[Open Questions]].

## Bağlam
PM panelinin iki personası bağımsız olarak aynı öneriye vardı: ilk ürün tam pazaryeri olmamalı; "odanı tara → ölçüyle doğru döşenmiş halini gör" deneyimi + ince bir lead katmanı olmalı (checkout yok). Kurucu aynı gün önce kararı erteledi ("henüz karar yok"), ardından kararı verdi.

## Karar
Kurucu (Selim, 2026-07-21): **"Şimdilik bu öneriyi benimse — ama ileride sepet ve checkout da gelecek."**
- İlk ürün kapsamı: oda tarama → gerçek ölçülü 3D görselleştirme + AI tasarım → ürün için **lead** aksiyonu.
- **Checkout/sepet ilk sürümde YOK**; ileride eklenecek (niyet net, zamanlama **To Be Decided**). Ödeme sağlayıcısının Iyzico olup olmayacağı da **belirsiz** — kurucu açıkça bunun henüz netleşmediğini belirtti (2026-07-21); Haziran'daki Faz 5d planı bir olasılık, taahhüt değil.

## Gerekçe
Teknoloji riski büyük ölçüde alınmışken ürün riski hiç alınmadı (0 dış kullanıcı, 0 satıcı, 3 test ürünü); doğrulanmamış talebe ödeme/iade/satıcı operasyonu altyapısı kurulmaz. Dar kapsam, kırılgan pipeline'ı sertleştirmeye ve ilk pazar temasına alan açar.

## Değerlendirilen Alternatifler
- Checkout dahil tam pazaryeri ile devam — reddedildi (şimdilik).
- Kararı test verisine erteleme — aynı gün içinde bu karara evrildi.

## Sonuçlar (Consequences)
- MVP tanımı bu kapsama göre yapılır; PM panelinin ilgili önerileri (lead birincil ticari metrik, tek satıcıdan 30-50 ürünlük katalog pilotu, moderated test) masada — bunlar hâlâ öneri, ayrıca kararlaştırılmalı.
- "Checkout or lead generation" akışı ilk sürüm için netleşti: **lead**. Gelir modeli detayı (komisyon / lead ücreti / abonelik) hâlâ **To Be Decided** — bkz. [[Marketplace Model]].
- Sepet/checkout geldiğinde ödeme sağlayıcısı (Iyzico dahil) o zaman kararlaştırılır — şimdilik açık.

## İlgili Bilgi
[[Product Overview]], [[Marketplace Model]], [[Open Questions]]

## Kaynak
[[2026-07-21 PM Panel Tartışması]] (moderatör sentezi + kurucu yanıtı)
