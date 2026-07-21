---
type: system
status: living
updated: 2026-07-20
---

# Glossary

> Projede kullanılan terimler. Yeni terim ortaya çıktıkça eklenir. Teknik terimler İngilizce tutulur.

## Ürün / pazar
- **brand-panel** — Satıcılar (SELLER/ADMIN) için web ürün yükleme paneli (Vite+React); 4 açı fotoğrafıyla ürün → otomatik 3D model.
- **LivaroTheme** — iOS tasarım sistemi (koyu kahve + altın, serif başlıklar, 5 sekme); tek doğruluk kaynağı `LivaroTheme.swift`.
- **Faz yapısı** — Proje fazlarla ilerliyor: Faz 1-2 (temel backend + Tripo3D pipeline, kayıt öncesi), Faz 3 (brand-panel ürün yükleme), Faz 4 (AI tasarımcı motoru), Faz 5a-5e (iOS; 5d sepet+ödeme, 5e TestFlight — henüz yapılmadı).
- **Iyzico** — Türkiye odaklı bir ödeme sağlayıcısı; Haziran'da Faz 5d için bir olasılık olarak düşünülmüştü ama kurucu bunun **henüz belirsiz** olduğunu belirtti (2026-07-21) — ödeme sağlayıcısı kararı açık.
- **Marketplace** — Alıcı ve satıcıları buluşturan pazaryeri.
- **Seller** — Mobilya ekleyip satan taraf.
- **Onboarding** — Kullanıcının/satıcının ürüne ilk giriş ve kurulum süreci.
- **Lead generation** — Satış yerine potansiyel müşteri iletişimi/ilgisi üretme modeli.
- **Prototype** — Erken deneme sürümü; iOS uygulaması + backend mevcut (bkz. [[Current State]]).
- **AI Designer** — Wizard: kullanıcı tarzı/bütçeyi seçer → pgvector semantik ürün arama + GPT-4o yerleşim koordinatları → tasarım sonucu.

## Tarama / 3D
- **RoomPlan** — Apple'ın LiDAR oda tarama API'si; duvar/kapı/pencere/obje + transform + dimensions verir. Taramanın temeli.
- **ARKit Scene Reconstruction** — LiDAR mesh üretimi (ARMeshAnchor); denendi, offline (bkz. [[ARKit Scene Reconstruction mesh + texture]]).
- **Gaussian Splatting (3DGS)** — Fotogerçekçi nokta-splat 3D gösterim; self-hosted gsplat denemesi rafta.
- **gsplat / nerfstudio / splatfacto** — Splat eğitim araç zinciri (self-hosted).
- **COLMAP** — Görüntülerden kamera pozu çıkaran SfM aracı; teşhis için kullanıldı (ARKit pozlarının yetersizliğini kanıtladı).
- **MetalSplatter** — iOS'ta .ply splat render kütüphanesi.
- **Transform(matrix:)** — RoomPlan 4x4 transform'unun RealityKit'te doğrudan kullanımı; render kuralı (bkz. karar 2026-07-09).
- **Dollhouse** — Dıştan bakışta kameraya bakan duvarları gizleme render tekniği.
- **Mirror tile** — Kırpılan fotoğraf parçasını 2x2 aynalayarak seamless'a yaklaştırma.
- **Yakın çekim (closeup)** — Zemin/duvara ~30-50 cm'den çekilen, doğrudan texture kaynağı fotoğraf (isteğe bağlı akış adımı).
- **USDZ / GLB** — 3D model formatları (USDZ: Apple QuickLook; GLB: glTF binary).
- **QuickLook** — iOS yerleşik USDZ görüntüleyici (kamera kısıtlanamaz).
- **PBR** — Physically Based Rendering materyali.
- **Keyframe projeksiyon** — Kamera karesinden mesh yüzeyine texture aktarımı.

## Altyapı / servisler
- **Modal** — Serverless GPU platformu; Blender render + splat eğitimi burada koşar.
- **R2** — Cloudflare nesne depolama (bucket `three-d-models`, public değil → **presigned URL** zorunlu).
- **Presigned URL** — Süreli imzalı erişim URL'si; iOS'a giden her R2 linki böyle olmalı.
- **Tripo3D** — Ürün görselinden 3D model üreten servis (`three-d-pipeline` kuyruğu).
- **flux-schnell** — Replicate'teki hızlı görüntü üretim modeli (texture fallback + render güzelleştirme).
- **gpt-image-1** — OpenAI görüntü üretimi (eski render yolu).
- **pgvector** — Postgres vektör arama uzantısı (semantik ürün arama).
- **mDNS** — `Selim-MacBook-Air.local` yerel ağ isim çözümü (dev backend bağlantısı).
- **xcodegen** — `project.yml`'den Xcode projesi üretimi (yeni dosyada şart).

> Not: Ürün adı "**Livaro**" repo/vault adıdır; ürünün nihai adı ekipçe teyit edilene kadar **Needs Validation**.
