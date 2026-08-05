---
type: decision
status: accepted
created: 2026-08-05
source: "[[2026-08-05 Build Oturumu — Admin Paneli Dilim 1]]"
related: ["[[Admin Panel]]", "[[2026-08-04 İşlem günlüğü ve sessiz olay defteri kabul edildi]]"]
---

# Ürün görüntüleme olayı saatte bir kez sayılır

## Bağlam

Sessiz olay defterinin dört tipinden biri "ürün görüntüleme". Bu olayın gerçek kullanıcı trafiğinde kaydedilebilmesi için Supabase edge function'a yazılması gerekiyor — orası **kimlik istemeyen, herkese açık** bir adres.

İnşa sırasındaki dal incelemesi iki sorun gösterdi:

1. **Sınırsız yazım yolu.** Repoda hız sınırlayıcı yok, tekilleştirme yok, saklama süresi yok. İsteyen biri bir döngüyle sonsuz satır yazdırıp Supabase depolamasını şişirebilir.
2. **Rakam şişiyor.** Aynı kişinin sayfayı 20 kez yenilemesi "20 görüntülenme" oluyor — pilot markaya söylenecek sayı yanıltıcı olur.

## Karar

**Aynı ziyaretçi + aynı ürün + aynı saat = tek kayıt.** Ziyaretçiyi ayırmak için IP adresinin şifreli özeti kullanılır; kimlik saklanmaz.

Bu şart, olay kaydı canlıya çıkmadan önce (Görev 10) uygulanacak.

## Gerekçe

Tek çözümle iki sorun birden kapanıyor: kötüye kullanma yolu daralıyor **ve** rakam dürüstleşiyor — "kaç kez açıldı"dan "kaç kişi baktı"ya yaklaşıyor. Kurucunun bu veriden beklediği şey zaten ikincisi (pilot markalara gösterilecek sayı).

## Değerlendirilen Alternatifler

- **Her şeyi say, 90 gün sonra sil** — depolama şişmesini çözerdi ama rakam yenilemelerle şişmeye devam eder ve kötüye kullanma anında hâlâ etkili olurdu. Reddedildi.
- **Şimdilik olduğu gibi bırak** — en az iş; ama rakama güvenilemez ve adres herkese açık olduğu için risk açık kalırdı. Reddedildi.

## Sonuçlar (Consequences)

- Görev 10'un (edge function'a olay kaydı ekleme) şartı bu; o iş bu tekilleştirme olmadan yayına alınmayacak.
- IP'nin şifreli özeti kullanıldığı için KVKK aydınlatma metninde olay kaydının anılması gereği değişmiyor (zaten [[2026-08-04 İşlem günlüğü ve sessiz olay defteri kabul edildi|4 Ağustos kararında]] kayıtlıydı).

## Riskler

- Aynı ağ arkasındaki farklı kullanıcılar (ofis, ev) tek ziyaretçi sayılabilir — sayı bir miktar düşük çıkar. Ham sayımın şişirmesine göre kabul edilebilir bir takas.

## Not: bu olay kişi bazlı DEĞİL

iOS ürün detayını kimlik göndermeden çekiyor, bu uçta kimlik doğrulama da yok. Yani **"kaç kez bakıldı" kaydedilir, "kim baktı" kaydedilmez.** Kişi bazlı görüntüleme istenirse iOS değişikliği + yeni sürüm gerekir — bu, [[2026-08-04 Kullanıcı kartı adminde — kişi bazlı kullanım verisi ve RoomPlan çıktısı|kullanıcı kartı kararını]] etkiler ve [[Open Questions]]'a yazıldı.

## İlgili Bilgi

[[Admin Panel]]

## Kaynak

[[2026-08-05 Build Oturumu — Admin Paneli Dilim 1]]
