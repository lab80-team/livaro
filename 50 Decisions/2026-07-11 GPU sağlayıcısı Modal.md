---
type: decision
status: accepted
created: 2026-07-11
source: "[[2026-07-16 Oturum Import — 3D Pipeline Evrimi]]"
related: []
---

# GPU sağlayıcısı Modal (RunPod değil)

## Bağlam
Gaussian Splat eğitimi için cloud GPU gerekiyordu; ilk plan RunPod Serverless idi.

## Karar
GPU sağlayıcı olarak **Modal** kullanılır. RunPod handler'ları Modal function'a çevrildi (`@app.function(gpu="T4")`), backend'de ModalService.

## Gerekçe
Kurucu (11.07): $30/ay ücretsiz kredi, kredi kartı gerektirmiyor, Docker build/push gerekmiyor (Modal Image).

## Sonuçlar (Consequences)
- Splat eğitimi (`gsplat/modal_app.py`) ve sonrasında Blender render (`blender/modal_blender.py`) da Modal'da koştu — karar kalıcılaştı.
- Deploy: `python3 -m modal deploy blender/modal_blender.py` (ve `gsplat/modal_app.py`).
- R2 erişimi Modal secret `livaro-r2` ile.
- Risk: kredi bitince workspace devre dışı kalıyor (13 Tem'de yaşandı; sonra çözüldü).

## İlgili Bilgi
[[System Architecture]], [[Deployment Strategy]]

## Kaynak
[[2026-07-16 Oturum Import — 3D Pipeline Evrimi]] (11.07: "RunPod değil Modal kullanacağız")
