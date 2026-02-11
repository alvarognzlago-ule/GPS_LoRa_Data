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

## Conclusiones Principales

* La **antena de mayor ganancia** reduce significativamente la pérdida de paquetes en zonas de sombra.
* Los valores de **SNR** demuestran la robustez de LoRa, permitiendo comunicación efectiva incluso con un RSSI inferior a -100 dBm.
* El entorno ("Tipo") es el factor determinante en la fluctuación de la precisión de la altitud GPS.
