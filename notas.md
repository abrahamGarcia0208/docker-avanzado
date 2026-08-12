# Módulo 4: Construcción de Imágenes Multiplataforma

## 🎯 ¿Qué es una Imagen Multiplataforma?
Es una imagen de Docker compilada simultáneamente para múltiples arquitecturas de procesador (como **AMD64** para procesadores Intel/AMD y **ARM64** para Apple Silicon, Raspberry Pi o servidores ARM en la nube).

Docker genera un **Índice de Manifiesto (Manifest List)** que empaqueta ambas variantes bajo el mismo nombre (*tag*). Cuando alguien hace `docker pull`, Docker detecta el procesador de la máquina en automático y descarga únicamente la versión compatible.

---

## 💻 El Comando Explicado Paso a Paso

```bash
docker build --platform=linux/amd64,linux/arm64 -t mi-imagen ./04-multi-platform

Desglose de cada parámetro:
docker build: Comando base de Docker para compilar una nueva imagen desde un Dockerfile.

--platform=linux/amd64,linux/arm64: La bandera clave. Le indica a Docker que genere dos arquitecturas en paralelo dentro del mismo proceso:

linux/amd64: Cubre la mayoría de computadoras tradicionales y servidores x86_64 (Intel/AMD).

linux/arm64: Cubre arquitectura ARM (Macs M1/M2/M3/M4, Raspberry Pi, AWS Graviton, tablets).

-t mi-imagen: Asigna un nombre o etiqueta (tag) a la imagen construida.

./04-multi-platform: Especifica la ruta del contexto de construcción (la carpeta donde está tu Dockerfile).