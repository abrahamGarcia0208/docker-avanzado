# Módulo 2: Escaneo de Vulnerabilidades (CVEs) y Seguridad en Imágenes

## 🛡️ Conceptos Clave
- **CVE (Common Vulnerabilities and Exposures):** Identificador público universal de una falla de seguridad conocida.
- **Score CVSS (0 - 10):**
  - 🚨 **Crítico (9.0 - 10.0):** Riesgo extremo, solución obligatoria.
  - 🔴 **Alto (7.0 - 8.9):** Atención prioritaria inmediata.
  - 🟡 **Medio (4.0 - 6.9):** Evaluar según el contexto.
  - 🟢 **Bajo (0.1 - 3.9):** Riesgo mínimo / aceptable.
- **Filosofía DevOps:** La meta NO es buscar 0 vulnerabilidades (es irreal e ineficiente), sino mitigar inteligentemente los riesgos de alto impacto (CVSS >= 7.0).

---

## 🐧 Herencia de Riesgo en Imágenes Base
- **Código de la Aplicación:** Rara vez trae vulnerabilidades directas del sistema operativo.
- **Imagen Base (`FROM`):**
  - **Ubuntu / Debian:** Pesadas (100 - 200 MB), traen muchas utilidades, pero heredan decenas de CVEs de fábrica.
  - **Alpine Linux:** Ultraligera (~5 MB), trae lo mínimo vital y reduce drásticamente la superficie de ataque.

---

## 💻 Comandos Útiles de Docker Scout

```bash
# Escaneo rápido de severidades (Críticas, Altas, Medias, Bajas)
docker scout quickview node:22-alpine

# Ver el detalle de todas las vulnerabilidades y versiones parcheadas
docker scout cves node:22-alpine