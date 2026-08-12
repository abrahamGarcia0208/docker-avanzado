# Módulo 3: Imágenes Distroless (Google Container Tools)

## 🎯 ¿Qué es una Imagen Distroless?
Es una imagen base construida por Google que contiene **únicamente tu aplicación y su runtime de ejecución** (Python, Node, Java, Go). 

No contiene:
- ❌ Shells (`/bin/sh`, `/bin/bash`).
- ❌ Gestores de paquetes (`apt`, `apk`, `yum`).
- ❌ Utilidades de sistema operativo (`curl`, `wget`, `ls`, `cd`).

---

## 📊 Beneficios Clave
- **Reducción de Tamaño:** Pasa de ~800 MB a ~50 MB (hasta un 94% más liviana).
- **Seguridad Máxima:** Si un atacante entra al contenedor, no tiene terminales ni herramientas para ejecutar exploits.
- **Velocidad:** Despliegues y descargas mucho más rápidos en orquestadores como Kubernetes o Google Cloud Run.

---

## ⚖️ ¿Cuándo usar Distroless?
- 🟢 **Producción:** Ideal para desplegar aplicaciones estables con la menor superficie de ataque posible.
- 🔴 **Desarrollo Local:** No se recomienda, ya que al no tener shell es imposible hacer `docker exec` para depurar en caliente.

---

## 🛠️ Estructura Multi-Stage Estándar (Python)

```dockerfile
# ETAPA 1: Construcción (Entorno con herramientas)
FROM python:3.11-slim AS build
WORKDIR /app
COPY hello.py .

# ETAPA 2: Producción (Distroless sin herramientas)
FROM gcr.io/distroless/python3-debian12
WORKDIR /app
COPY --from=build /app /app

CMD ["hello.py"]