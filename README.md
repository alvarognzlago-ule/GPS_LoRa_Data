# LoRa GPS Tracking - Análisis de Propagación y Rendimiento

Este repositorio contiene un conjunto de datos recopilados durante pruebas de campo para evaluar el rendimiento de la tecnología **LoRa** en la transmisión de coordenadas **GPS** en tiempo real. Se analizan variables críticas de red y la influencia del hardware (antenas) en la calidad del enlace.

## Descripción de los Datos

Los datos están divididos en tres archivos principales que representan diferentes sesiones de prueba:

* **Antena Pequeña:** Datos iniciales de referencia con hardware compacto.
* **Antena Grande (v1 y v2):** Pruebas de rendimiento utilizando una antena de mayor ganancia para evaluar la mejora en el alcance y estabilidad.

### Columnas en los Archivos CSV:
| Columna | Descripción |
| :--- | :--- |
| `Timestamp` | Fecha y hora del paquete recibido. |
| `Latitud/Longitud` | Coordenadas geográficas obtenidas por el GPS. |
| `Altitud` | Altura sobre el nivel del mar (m). |
| `SNR` | Signal-to-Noise Ratio (Relación señal-ruido en dB). |
| `RSSI` | Received Signal Strength Indicator (Potencia de señal recibida en dBm). |
| `Tipo` | Etiqueta de entorno (ej. "interior" o exterior). |

## Visualizaciones

El proyecto incluye análisis visuales de la degradación de la señal respecto a la distancia:

1.  **RSSI vs Distancia:** Muestra cómo disminuye la potencia de la señal a medida que el nodo se aleja del gateway.
2.  **SNR vs Distancia:** Evalúa la calidad de la modulación y la capacidad de demodulación bajo condiciones de ruido.

## Hardware Utilizado

* **Módulo LoRa:** (Ej: Semtech SX1276 / Heltec WiFi LoRa 32)
* **Módulo GPS:** (Ej: NEO-6M / NEO-8M)
* **Antenas:** Comparativa entre antena monopolo de 2dBi (pequeña) vs antena de alta ganancia (grande).

## Valoración Técnica de los Datos

### 1. Comparativa de Antenas
Se observa una diferencia clara en la estabilidad de la señal entre los dispositivos probados. La **"antena grande"** muestra, en general, valores de **RSSI** (fuerza de la señal) más consistentes en distancias mayores en comparación con la antena pequeña, lo que sugiere una mayor ganancia y mejor capacidad de recepción en el límite del alcance.

### 2. Calidad de Señal (SNR vs. RSSI)
Las gráficas revelan un comportamiento robusto de la tecnología LoRa:
* Aunque el **RSSI** decae progresivamente con la distancia, el **SNR** (*Signal-to-Noise Ratio*) se mantiene en niveles positivos o cercanos a cero en la mayoría de los puntos exteriores.
* Esto es fundamental, ya que demuestra la capacidad de LoRa para **decodificar paquetes incluso por debajo del nivel de ruido**, manteniendo la comunicación donde otras tecnologías fallarían.

### 3. Comportamiento en Interiores
Los datos etiquetados como **"interior"** muestran una degradación esperada en dos frentes críticos:
* **Señal LoRa:** Caídas notables y abruptas en el RSSI debido a la atenuación producida por obstáculos físicos (muros, forjados).
* **Precisión GPS:** Inestabilidad en las lecturas, especialmente visible en las **altitudes variables**, causadas por el efecto *multipath* (rebote de señal) y la falta de línea de visión directa con los satélites.

### 4. Precisión y Entorno GPS
Los registros se realizaron un entorno de pruebas con desafíos estructurales (campus):
* **Fluctuaciones de Altitud:** Se observan variaciones típicas de receptores GPS comerciales cuando no existe una línea de visión perfecta (**LOS - *Line of Sight***).
* **Consistencia Geográfica:** A pesar de las variaciones de altitud, el posicionamiento horizontal (latitud/longitud) se mantiene suficientemente estable para aplicaciones de seguimiento y monitorización de activos.

## Conclusiones Principales

* La **antena de mayor ganancia** reduce significativamente la pérdida de paquetes en zonas de sombra.
* Los valores de **SNR** demuestran la robustez de LoRa, permitiendo comunicación efectiva incluso con un RSSI inferior a -100 dBm.
* El entorno ("Tipo") es el factor determinante en la fluctuación de la precisión de la altitud GPS.
