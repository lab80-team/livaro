---
type: decision
status: accepted
created: 2026-07-28
source: "[[2026 07 28 Thinking Session — Mağaza Web Paneli User Journey]]"
related: ["[[Seller Experience]]"]
---

# Mağaza kaydı self-serve + admin onayı

## Bağlam
Satıcı onboarding'inin davet mi self-serve mi olacağı açıktı ([[Seller Experience]]). PM'ler pilot için "sitede yalnız başvuru formu; hesabı kurucular elle açsın" önerdi.

## Karar
- **Self-serve kayıt MVP'de var** (PM önerisi reddedildi): mağaza sahibi web sitesinde "Kaydol" ile e-posta, telefon, ad-soyad, mağaza adı, şehir, ilçe ve kategori(ler) bilgilerini girer.
- Kayıtta **şifre** belirlenir; panel girişinde **telefona SMS kodu da** kullanılabilir (iki giriş yöntemi).
- Kayıtta **KVKK aydınlatma onay kutusu** + **satıcı sözleşmesi onay kutusu** (%10 komisyon, nakliye sorumluluğu gibi şartların hukuki dayanağı).
- **Opsiyonel alan:** mağazanın web sitesi / Instagram'ı (sahtelik filtresi).
- Kaydol sonrası **kuruculara e-posta** gider; mağaza **net beklentili "onaya gönderildi" ekranı** görür; **onay/red e-postası** gönderilir; onayla hesap açılır.
- Yasal belgeler (vergi levhası, vergi dairesi vb.) **MVP'de istenmez**; ileride istenecek.

## Gerekçe
Kurucu, kayıt kapısını baştan self-serve kurmak istiyor; admin onayı sahte/niteliksiz mağaza filtresi olarak yeterli görülüyor. Sözleşme ve KVKK kutuları PM uyarısıyla eklendi (sözleşmesiz mağazadan komisyon istemenin dayanağı olmaz).

## Değerlendirilen Alternatifler
- Başvuru formu + hesabı kurucuların elle açması (iki PM'in ortak önerisi) — reddedildi.
- Yalnız SMS ile giriş (şifresiz; PM önerisi) — reddedildi, şifre + SMS ikisi de olacak.

## Riskler
- Onay/red kriterleri tanımsız → [[Open Questions]].
- İki giriş yöntemi ekstra geliştirme işi + "şifremi unuttum" destek yükü (PM notu).

## Kaynak Toplantı
[[2026 07 28 Thinking Session — Mağaza Web Paneli User Journey]] (PM tartışması: [[2026-07-28 PM Tartışması — Mağaza Paneli Journey]])
