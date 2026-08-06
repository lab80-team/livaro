---
type: decision
status: accepted
created: 2026-08-06
source: "[[2026 08 06 Thinking Session — Uygulama User Journey]]"
related: []
---

# Giriş ekranı ilk ekran; misafir gezinme serbest kalır

## Bağlam
[[2026-06-22 iOS uygulaması yalnızca müşteri tarafı]] ve 24 Temmuz teyidi "açılışta login zorunlu değil" diyordu; 24 Temmuz'da bir **welcome page** vizyonu vardı (güzel ev arka planı + "Odayı Tara"/"Projelerim"). Ama 28 Temmuz'da giriş sistemi genişletilirken açılışa **giriş ekranı** kondu ve bugün kodda öyle çalışıyor. Karar notu güncellenmemişti.

## Karar
1. **İlk ekran giriş ekranıdır.** Üç seçenek: **Apple**, **Google**, **telefon numarası**. En altta küçük yazıyla **"Misafir olarak devam et"**.
   - "Android ile giriş" **Google hesabıyla giriş** demektir; ayrı bir Android uygulaması yazılmayacak, uygulama iPhone'da kalıyor.
2. **Misafir gezinme serbest kalıyor**: Keşfet ve ürün detayı açık.
3. **Duvar nerede**: "Odayı Tara", kalp (favori) ve sepete ekleme butonuna dokununca **işlem başlamadan önce** giriş kartı çıkar. Misafir 3-4 dakika oda tarayıp emeğini kaybetmez.
4. Misafir butonunun altına tek satır: "Oda taramak ve tasarımları kaydetmek için giriş gerekir."
5. Welcome page vizyonu **rafta**: ilk ekran artık giriş ekranı.

## Gerekçe
- Kurucunun açık tercihi; ayrıca kodda zaten çalışıyor (yeni iş değil).
- Misafirin işini yarıda kaybetmesi, uygulamayı sildiren türden bir andır — bu yüzden giriş isteği **işlem başlamadan** çıkar, sonunda değil.

## Değerlendirilen Alternatifler
- **Değer önce, giriş sonra** (welcome page + katalog serbest): bir yönetici bunu önerdi (hiç tanınmayan bir uygulamada değer görülmeden hesap istemek en büyük kayıp noktası). Kurucu giriş ekranını seçti.
- **Misafir tarayabilsin ama kaydedemesin**: emek kaybı riski nedeniyle reddedildi.
- **Misafir sadece baksın**: gereksiz kısıt.

## Sonuçlar (Consequences)
- [[2026-06-22 iOS uygulaması yalnızca müşteri tarafı]] kararının "açılışta login zorunlu değil" kısmı **güncellendi**; misafir gezinme serbestliği duruyor.
- Kalp ve sepete ekleme butonlarına giriş kontrolü eklenecek (bu özellikler henüz hiç yok).

## Riskler
- **Telefonla giriş gerçek kullanıcıda henüz çalışmıyor**: Twilio hesabı hâlâ deneme modunda, yalnız doğrulanmış numaralara SMS gidiyor. Giriş ekranı ilk ekransa bu, kapıyı kısmen kilitli bırakır — pilottan önce Twilio hesabı deneme modundan çıkarılmalı.
- İnternetsiz açılışta giriş ekranının davranışı hâlâ açık → [[Open Questions]].

## İlgili Görevler
→ [[Task Board]]

## İlgili Bilgi
[[User Onboarding]]

## Kaynak Toplantı
[[2026 08 06 Thinking Session — Uygulama User Journey]]
