# CLAUDE.md — Livaro Vault

Bu, **Livaro** (online mobilya pazaryeri) projesinin Obsidian vault'u ve ortak proje hafızasıdır. Bu dosya, vault'ta çalışan herkes (ve AI ajanı) için pratik kılavuzdur.

## Amaç
Ekip için tek bir çalışma alanı: toplantılar, bilgi, deneyler, kararlar, planlar ve görevler. Fikirleri karar, hipotezleri gerçek gibi göstermeden ilerlemeyi belgelemek.

## Klasör Yapısı
- `00 System/` — Home, Project Brief, Current State, Open Questions, Glossary, How We Work, `Templates/`
- `10 Inbox/` — ham notlar, işlenmemiş içerik
- `20 Meetings/` — toplantı log'ları (kaynak) + `Meeting Index`
- `30 Knowledge/` — güncel bilgi: `Product/`, `Users/`, `Marketplace/`, `Engineering/`, `Room Scanning/`
- `40 Experiments/` — teknik ve ürün deneyleri (çalışan + başarısız) + `Experiment Index`
- `50 Decisions/` — açık kararlar + `Decision Index`
- `60 Planning/` — Roadmap, Product Flows, Technical Plan, Launch Checklist
- `70 Tasks/` — `Task Board` + büyük görev notları
- `80 People/` — kişi notları
- `90 Archive/` — eskimiş içerik

## Altı Türü Ayır
1. **Kaynak** (toplantı, inbox, import) — silinmez, anlamı değiştirilmez.
2. **Bilgi** (`30 Knowledge/`) — şu an doğru sandığımız şeyler; evrildikçe güncellenir.
3. **Deney** (`40 Experiments/`) — testler; başarısızlar dahil.
4. **Karar** (`50 Decisions/`) — ekibin **açıkça** verdiği kararlar.
5. **Plan** (`60 Planning/`) — roadmap, akışlar, teknik plan.
6. **Görev** (`70 Tasks/`) — birinin yapacağı somut iş.

> Fikir ≠ karar. Hipotez ≠ gerçek. Öneri, karar notuna değil; ürün/plan notuna veya `Open Questions`'a gider.

## Yeni Toplantı Nasıl İşlenir
1. `00 System/Templates/Meeting Template` ile `20 Meetings/YYYY MM DD Konu.md` oluştur.
2. İçe aktarılan içeriği **Ham Notlar**'a birebir koy. Sadece bariz format sorunlarını düzelt; **anlamı değiştirme**.
3. **Tartışma Özeti**'ni yaz.
4. İlgili mevcut `30 Knowledge/` notlarını **güncelle** (yeni not açma — aşağıya bak).
5. Yalnızca **açık** kararlar için `50 Decisions/` notu aç, `Decision Index`'e ekle.
6. Anlamlı testler için `40 Experiments/` notu aç, `Experiment Index`'e ekle.
7. **Açıkça söylenmiş** görevleri `70 Tasks/Task Board`'a ekle.
8. `Current State` ve `Open Questions`'ı güncelle.
9. Oluşturulan/güncellenen her notu toplantıya (ve tersi) **linkle**.

## Current State Nasıl Güncellenir
- `Current State` = projenin **şu anki** özeti, **tarihçe değil**. Geçmiş, toplantılarda ve Git'te durur.
- Her toplantı işlemesinden sonra: ürün/teknik/room-scanning durumu, çalışan/başarısız bileşenler, öncelikler, blocker'lar, son kararlar bölümlerini gerçeğe göre güncelle. Kısa ve pratik tut.

## Duplicate Not Açma
- Yeni not açmadan önce ara: konu için mevcut bir bilgi notu varsa **onu güncelle**.
- Aynı konu hakkında ikinci not yaratma. Aynı şeye işaret eden iki isim varsa alias kullan.
- Grafiği "yoğun göstermek" için link/not ekleme.

## Belirsizliği Koru
- Bilinmeyeni açıkça işaretle: `Unknown`, `To Be Decided`, `Needs Validation`.
- Cevabı kanıt/karar olmadan uydurma. Cevaplanmamış soru → `Open Questions`.
- İki kaynak çelişiyorsa çelişkiyi **kaydet**; kanıt/karar olmadan birini seçme.

## Kaynak Linklerini Koru
- Toplantı ve import'lar işlendikten **sonra da silinmez**.
- Bilgi önemli ölçüde değişince, **neden** değiştiğini açıklayan kaynak linklerini koru.
- Linkleme: toplantı ↔ karar/görev/deney/bilgi; karar → kaynak toplantı; deney → toplantı + ilgili teknik bilgi; görev → kaynağı olan toplantı/karar.

## Uydurma Yasağı
- **Owner, deadline, karar veya gerçek uydurma.** Yalnızca açıkça belirtilmişse yaz.
- Genel startup tavsiyesi yazma; yalnızca bu projenin bağlamını kullan.

## Templates
`00 System/Templates/` altında: Meeting, Knowledge, Experiment, Decision, Task, Person. Basit YAML kullan; boş property ekleme.

## Git
- Bu vault versiyonlanır. Tarihçe için Git geçmişine güven.
- `.obsidian/` workspace ayarları ve `.DS_Store` git'e girmez (bkz. `.gitignore`).
