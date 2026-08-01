---
type: import
date: 2026-08-02
status: processed
related: ["[[2026-07-31 Kategori 3D Stratejisi, Tripo Kredi Ölçümü, iOS Doku Düzeltmesi ve Main Merge]]"]
---

# Güvenlik Düzeltmeleri — Oda Taraması Sahipliği ve Render Kilidi (2026-08-02)

> Kaynak: kod reposu (`~/Desktop/livaro`), main `44a4497 → 0477596` (7 commit, ff-merge + push). 31 Tem merge incelemesinin "pilot öncesi kapatılmalı" dediği iki ayrı iş, kurucunun seçimiyle bu oturumda kapatıldı. Toplantı değil — chat üzerinden yürütülen düzeltme oturumu.

## 1. AI aramada oda taraması sahiplik kontrolü (KVKK) — KAPANDI

- **Açık neydi:** `POST /ai/designer/search`, gönderilen `roomScanId`'nin istekteki kullanıcıya ait olup olmadığına bakmıyordu. Giriş yapmış herhangi bir kullanıcı başkasının ev geometrisini (duvar/kapı/pencere) sisteme kullandırabiliyor, o veri OpenAI'a giden prompt'a giriyordu. Temmuz'dan kalma kod; 2026-07-31 merge turunda bulunmuştu.
- **Düzeltme:** repo'nun yerleşik sahiplik deseni (design-result.create ile aynı): tarama istekteki kullanıcıya ait değilse **bilgi sızdırmayan 404** (403 değil — kaydın varlığı bile açık edilmez). Sahiplik geçmeden hiçbir OpenAI çağrısı yapılmıyor; test bunu ayrıca doğruluyor.
- Edge function'da bu uç yok (501 döner) — düzeltme yalnız Nest backend'de.

## 2. Blender render mükerrer tetikleme koruması atomik — KAPANDI

- **Açık neydi:** koruma salt oku-sonra-davran'dı (R2'deki job.json'a bak → "iş yok" ise başlat). İki eşzamanlı POST ikisi de kontrolü geçip aynı **ücretli** Modal işini iki kez koşturabiliyordu.
- **Düzeltme:** `design_results` tablosuna `renderClaimedAt` kolonu (migration `20260801212253`, uygulandı, DB senkron). Tetikleme artık repo'nun CAS deseniyle atomik üstleniliyor; kaybeden Modal'a hiç dokunmadan RUNNING döner. Katmanlar:
  - Pahalı Modal çağrısından hemen önce **fence**: kilit hazırlık sırasında devralındıysa iptal.
  - Spawn çağrısına **3 dk kesin zaman aşımı** (kilit kirası 10 dk'nın altında; eskiden sınırsız asılı kalabiliyordu).
  - **Belirsiz-başlangıç koruması**: zaman aşımı ya da "sunucu 2xx döndü ama cevap çözülemedi" durumlarında iş başlamış olabilir → kilit tutulur (para koruması). Net hatada kilit bırakılır, retry açık kalır. Çökmüş çalıştırmanın kilidi 10 dk sonra bayat sayılır.
  - Yan bulgu kapandı: cevapta `call_id` yoksa eskiden **sessizce geçersiz kayıt** yazılıyordu; artık hata.
- **Bilinçli kalıntı risk (kodda belgeli):** bağlantının tam kabul anında kopması (çok dar pencere) hâlâ çift render'a yol açabilir — kapatmanın maliyeti (her Modal kesintisinde retry'ı 10 dk kilitlemek) riskin kendisinden pahalı.

## Doğrulama

- TDD: her düzeltme önce hatayı kanıtlayan kırmızı testle yazıldı; **415 test yeşil** (önceki 399 + 16 yeni), dört derleme temiz, yeni spec dosyaları lint-temiz.
- Codex inceleme kapısı: **6 tur**; her turun bulguları işlendi (fence, timeout, belirsiz-start, maskesiz release); son karar **"merge-ready"**. Repo genelindeki eski format borcu bilinçli elde bırakıldı (main'de de aynı dosyalar lint geçmiyor; merge çıtası değil).
- Yan tespit: Task Board'daki "`drop_splat_and_ai_task` migration'ını uygula" görevi bayatlamış — `prisma migrate status` (2026-08-02) 13 migration'ın tamamının uygulandığını, şemanın senkron olduğunu söylüyor.

## İşlendiği notlar

[[Task Board]], [[Current State]], [[Open Questions]]
