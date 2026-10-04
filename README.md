# 🔍 IOC Reputation Analyzer

**IOC Reputation Analyzer** es una herramienta en Python que permite analizar Indicadores de Compromiso (IOCs) —como direcciones IP, dominios, URLs y hashes de archivos— consultando su reputación a través de la API de [VirusTotal](https://www.virustotal.com/).

El resultado del análisis incluye estadísticas de detección por motores antivirus y se exporta a un archivo Excel con visualizaciones y estadísticas detalladas.

---

## 📂 Estructura del Proyecto

```
reputacion_ioc.py         # Script principal del analizador
indicadores.txt           # Archivo de entrada con los IOCs (uno por línea)
resultados_iocs.xlsx      # Archivo de salida con los resultados (generado automáticamente)
```

---

## 🚀 Funcionalidades

- Clasificación automática de IOC (hash, IP, dominio, URL)
- Consulta de reputación usando la API pública de VirusTotal
- Análisis en paralelo con hilos (para mayor velocidad)
- Exportación de resultados a Excel
- Visualizaciones automáticas con Matplotlib y Seaborn

---

## 📋 Requisitos

Antes de ejecutar el script, asegúrate de tener instaladas las siguientes dependencias de Python:

```bash
pip install -r requirements.txt
```

También necesitas:

- Una cuenta en [VirusTotal](https://www.virustotal.com/gui/join-us) para obtener una API Key gratuita.
- Un archivo de texto `indicadores.txt` con los IOCs a analizar, uno por línea.

---

## 🛠️ Configuración

La API key **no se escribe en el código**: el script la lee desde la variable de entorno `VT_API_KEY`.

```bash
# Linux / macOS / WSL
export VT_API_KEY="tu_api_key_de_virustotal"

# Windows (PowerShell)
$env:VT_API_KEY="tu_api_key_de_virustotal"
```

Opcionalmente, puedes ajustar estas constantes en `reputacion_ioc.py`:

```python
INPUT_FILE = "indicadores.txt"          # Ruta al archivo de entrada
OUTPUT_FILE = "resultados_iocs.xlsx"    # Nombre del archivo de salida
MAX_THREADS = 5                         # Número de hilos para ejecución en paralelo
```

---

## ▶️ Uso

Ejecuta el script desde consola:

```bash
python reputacion_ioc.py
```

El script:

1. Lee los IOCs desde `indicadores.txt`.
2. Clasifica y consulta cada IOC en VirusTotal.
3. Genera un archivo `resultados_iocs.xlsx` con los resultados.
4. Muestra estadísticas y gráficos en pantalla.

---

## 📈 Ejemplo de salida

- Tabla con columnas:
  - `ioc`, `type`, `last_analysis_date`, `positive_engines`, `total_engines`, `score`
- Estadísticas por tipo de IOC
- Gráfico de distribución de tipos de IOC

---

## 🧠 Notas

- Se ignoran líneas vacías y comentarios (que empiecen con `#`) en `indicadores.txt`.
- Si excedes el límite de consultas de la API, el script esperará automáticamente.
- La puntuación (`score`) representa el porcentaje de motores que detectan el IOC como malicioso.

---

## ✉️ Contacto

¿Tienes sugerencias o preguntas? ¡Contribuciones y mejoras son bienvenidas!
