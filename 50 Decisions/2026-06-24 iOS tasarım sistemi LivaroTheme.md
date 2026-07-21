---
type: decision
status: accepted
created: 2026-06-24
source: "[[2026-07-08 Oturum Import — Web Temelleri ve iOS Başlangıcı]]"
related: []
---

# iOS tasarım sistemi: LivaroTheme (lüks/sıcak kimlik, 5 sekme)

## Bağlam
Faz 5b sonrası iOS ekranları çoğalırken görsel tutarlılık için kurucu ayrıntılı bir tasarım spec'i verdi (24 Haz) ve mockup'a göre revize etti.

## Karar
Kurucunun birebir spec'i — tüm yeni ekranlar `LivaroTheme.swift`'ten (tek doğruluk kaynağı) beslenir:
- **Renkler**: arka plan `#1A1612` (çok koyu kahve), kart `#2A2420`, vurgu/CTA `#C9A96E` (altın), ikincil metin `#8A8078`, birincil metin `#F5F0EB`.
- **Font**: başlıklar serif (Georgia/sistem serif), gövde sistem sans-serif.
- **Bileşenler**: kart cornerRadius 16 + `white.opacity(0.08)` border + 16 padding; birincil buton altın zemin + koyu metin; ikincil buton şeffaf + altın border.
- **Navigasyon**: **5 sekme** — Ana Sayfa, Keşfet, Favoriler, Sepet, Profil. "Odalarım" sekme DEĞİL; Ana Sayfa'daki "Odayı Tara" (altın CTA) + "Projelerim" (secondary) butonlarından erişilir. HomeView: büyük serif "Livaro" + "Hayalindeki mekanı tasarla".
- **Kurallar**: 8px spacing grid; 200-300ms smooth animasyonlar; tüm tıklanabilirlerde haptic; min 44×44pt dokunma alanı; tüm metin Türkçe; Apple HIG uyumu; genel his "lüks mobilya markası, premium, sıcak tonlar".

## Gerekçe
Premium marka algısı; brand-panel'in "Sıcak/Lüks" web kimliğiyle (koyu kahve + altın) tutarlılık.

## Sonuçlar (Consequences)
- Mevcut tüm ekranlar temaya migre edildi (25 Haz, 20 commit); sonraki her ekran temadan besleniyor.

## İlgili Bilgi
[[Product Overview]], [[Seller Experience]] (web kimliği)

## Kaynak
[[2026-07-08 Oturum Import — Web Temelleri ve iOS Başlangıcı]] (24 Haz mesajı, birebir spec)
