---
type: knowledge
status: living
updated: 2026-07-20
related: []
---

# Deployment Strategy

## Şu An Bilinenler (geliştirme ortamı — production değil)
- **Backend (dev)**: kurucu Mac'inde `REDIS_URL="redis://localhost:6379" npm run start:dev`; telefon **mDNS** ile bağlanır: `http://Selim-MacBook-Air.local:3000/api` (IP değişse de kırılmaz; `NSLocalNetworkUsageDescription` gerekli).
- **iOS (dev)**: `cd ios && xcodegen generate` → `xcodebuild -destination 'id=00008140-000615110286801C'` → `xcrun devicectl device install/launch`. Cihaz crash raporları: `python3 -m pymobiledevice3 crash pull`.
- **Modal**: `python3 -m modal deploy blender/modal_blender.py` (ve `gsplat/modal_app.py`); R2 erişimi Modal secret `livaro-r2`; endpoint'ler proxy-auth (Modal-Key/Modal-Secret).
- **Veritabanı**: Supabase Postgres (pooler). **Depolama**: Cloudflare R2 (presign zorunlu).
- Git: kod reposunda iş `wip-mesh-pipeline` branch'inde toplandı (16 Tem itibarıyla main'e merge edilmemişti; 19-20 Tem'de push yapıldı — merge durumu **Needs Validation**).

## Varsayımlar
- Prototip fazında tek geliştirici Mac'i + Modal + Supabase + R2 yeterli.

## Bilinmeyenler
- **Production deployment tamamen açık**: backend hosting, ortamlar (staging/prod), CI/CD, App Store/TestFlight süreci — **To Be Decided**.
- Modal maliyet modeli ölçekte — **Unknown**.

## Önemli Sorular
- İlk dış kullanıcı testi için backend nereye deploy edilecek (Mac'e bağımlılık kalkmalı)?
- TestFlight dağıtımı ne zaman başlamalı?

## İlgili Notlar
- [[System Architecture]]
- [[Known Pitfalls]]
- [[Launch Checklist]]
- [[60 Planning/Technical Plan|Technical Plan]]

## Kaynaklar
- `~/Desktop/livaro/PROJECT_STATUS.md`
- [[2026-07-16 Oturum Import — 3D Pipeline Evrimi]]
