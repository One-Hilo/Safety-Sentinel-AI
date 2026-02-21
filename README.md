````md
# 🛡️ Safety-Sentinel-AI — Detector de Casco con Visión Artificial

**Safety-Sentinel-AI** es un proyecto de visión artificial orientado a **seguridad laboral** que detecta automáticamente si una persona **lleva casco** o **no lleva casco** en entornos industriales, obras, almacenes y zonas de riesgo.

Este repositorio es la base para integrar el detector con tu plataforma/app (**amadorcristaleria.onehilo.com**) o cualquier sistema de vigilancia, alertas y auditoría de seguridad.

---

## ✅ Qué have

- Detecta **personas** y clasifica **uso de casco** (Helmet / No-Helmet)
- Procesa:
  - Imágenes (JPG/PNG)
  - Vídeos (MP4)
  - Cámaras (RTSP / webcam)
- Genera resultados listos para:
  - Alertas
  - Registro de eventos
  - Panel de control / dashboard
  - Integración con APIs

---

## 🧩 Casos de uso

- Control automático de EPIs en obras y fábricas
- Auditoría y trazabilidad de seguridad
- Alertas en tiempo real en accesos a zonas de riesgo
- Integración con cámaras IP (Hikvision, Dahua, etc.)

---

## ⚙️ Requisitos

- Windows / Linux / macOS
- **Python 3.9+** (recomendado)
- Opcional: GPU NVIDIA + CUDA (para tiempo real)

---

## 🚀 Instalación (entorno virtual)

### 1) Clona el repo

```bash
git clone https://github.com/One-Hilo/Safety-Sentinel-AI.git
cd Safety-Sentinel-AI
```
````

### 2) Crea y activa entorno

**Windows**

```bash
python -m venv .venv
.venv\Scripts\activate
```

**Linux/Mac**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3) Instala dependencias

```bash
pip install -U pip wheel
pip install ultralytics opencv-python
```

> Si tienes un `requirements.txt` en el repo, usa:

```bash
pip install -r requirements.txt
```

---

## 🧠 Modelos

Puedes usar YOLO preentrenado y luego afinar con tu dataset:

- Para empezar rápido: `yolov8n.pt` / `yolov8s.pt`
- Para producción: entrenar un modelo con clases:
  - `helmet`
  - `no_helmet`

---

## ▶️ Uso rápido

### 1) Predicción sobre una imagen

```bash
yolo predict model=TU_MODELO.pt source="ruta/a/imagen.jpg"
```

### 2) Predicción sobre un vídeo

```bash
yolo predict model=TU_MODELO.pt source="ruta/a/video.mp4"
```

### 3) Predicción desde cámara / RTSP

```bash
yolo predict model=TU_MODELO.pt source="rtsp://usuario:pass@IP:554/stream"
```

---

## 🧪 Ejemplo en Python (script mínimo)

Crea un archivo `predict.py`:

```python
from ultralytics import YOLO

model = YOLO("TU_MODELO.pt")  # por ejemplo: runs/detect/train/weights/best.pt
results = model.predict(source="ruta/a/imagen_o_video", conf=0.25)

# Mostrar resultados
for r in results:
    r.show()
```

Ejecuta:

```bash
python predict.py
```

---

## 📦 Exportar a ONNX (para producción)

```bash
yolo export model=TU_MODELO.pt format=onnx
```

---

## 🔌 Integración con tu plataforma/app

Este repositorio está pensado para que puedas conectarlo con tu app:

- **amadorcristaleria.onehilo.com**
- Dashboard y alertas
- API para registrar detecciones:
  - timestamp
  - cámara / ubicación
  - bbox
  - clase (helmet/no_helmet)
  - confianza

> Si quieres, puedo prepararte una carpeta `/api` con un servidor FastAPI para recibir frames o URLs y devolver detecciones en JSON.

---

## 🛠️ Roadmap

- [ ] Entrenamiento con dataset propio (helmet / no_helmet)
- [ ] Modo “evento” (solo guardar cuando hay _no_helmet_)
- [ ] Guardado de evidencias (imagen/clip + bbox)
- [ ] API REST (FastAPI) para integración
- [ ] Docker para despliegue
- [ ] Soporte multi-cámara

---

## 📜 Licencia

Este proyecto puede utilizar modelos y dependencias con licencias distintas (por ejemplo Ultralytics/YOLO).
Revisa `LICENSE` y las licencias de los modelos/datasets que uses antes de desplegar en producción.

---

## 📩 Contacto

\*\*One-Hilo
