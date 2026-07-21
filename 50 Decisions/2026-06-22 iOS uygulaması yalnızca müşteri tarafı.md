---
type: decision
status: accepted
created: 2026-06-22
source: "[[2026-07-08 Oturum Import — Web Temelleri ve iOS Başlangıcı]]"
related: []
---

# iOS uygulaması yalnızca müşteri (CUSTOMER) tarafı; satıcılar brand-panel'de

## Bağlam
Faz 5 (iOS uygulaması) kapsamı belirlenirken rollerin (CUSTOMER/SELLER/ADMIN) hangi yüzeyde yaşayacağı netleştirilmeliydi.

## Karar
Kurucu (22 Haz, AskUserQuestion yanıtı: "Evet, sadece CUSTOMER"):
- iOS uygulaması **yalnızca müşteri deneyimi**; kayıt olan herkes CUSTOMER (rol seçimi yok).
- Satıcı (SELLER) ve ADMIN işleri **brand-panel web** arayüzünde kalır (brand-panel'e CUSTOMER giremez).
- **Misafir gezinme serbest**: iOS açılışta login zorunlu değil; ürün listesi doğrudan görünür, kişisel aksiyonlarda auth istenir.
- iOS 17+ minimum; "Sepete Ekle" gibi henüz işlevsiz butonlar placeholder olarak bile gösterilmez (YAGNI).

## Gerekçe
İki tarafın ihtiyaçları farklı; satıcı araçları web'de zaten kurulu (Faz 3). Tek platformda rol karmaşası yerine net ayrım.

## Sonuçlar (Consequences)
- Satıcı deneyimi = [[Seller Experience]] (web); müşteri deneyimi = iOS.
- O tarihte sepet/ödeme (Iyzico) Faz 5d'ye planlanmıştı; TestFlight Faz 5e — henüz yapılmadı. **Güncelleme (2026-07-21):** ödeme sağlayıcısının Iyzico olup olmayacağı kurucu tarafından açıkça belirsiz ilan edildi — bkz. [[2026-07-21 İlk ürün kapsamı görselleştirme + lead]], [[Marketplace Model]].

## İlgili Bilgi
[[Marketplace Model]], [[User Onboarding]]

## Kaynak
[[2026-07-08 Oturum Import — Web Temelleri ve iOS Başlangıcı]] (22 Haz mesajları)
