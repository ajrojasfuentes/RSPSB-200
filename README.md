# Refined Spanish Paragraph Simplification Benchmark – 200 (RSPSB-200)

Este documento describe la estructura, estadísticas y uso del corpus **RSPSB-200**, así como las correcciones y aclaraciones aplicadas a su documentación original.

---

## 1. Descripción general del corpus

- **Nombre:** Refined Spanish Paragraph Simplification Benchmark – 200 (RSPSB-200).
- **Origen:** Muestreo aleatorio estratificado de 200 pares de párrafos extraídos del corpus SPSB-5K.
- **Versión del LLM utilizado para refinamiento:** Claude Sonnet 4.1 (OpenAI).
- **Objetivo:**  
  - Banco de pruebas para tareas de simplificación y complicación de texto en español.  
  - Entrenamiento y evaluación de modelos de simplificación y métricas de legibilidad.

---

## 2. Estructura del archivo CSV

- **Formato:** CSV UTF-8.
- **Filas:** 200 registros más la fila de encabezado.
- **Columnas:**
  1. `original` (string): párrafo original.
  2. `simplificado` (string): versión simplificada o complicada del párrafo.
  3. `calidad_de_simplificacion` (float): puntuación entre 0.0000 y 1.0000.

---

## 3. Estadísticas descriptivas

| Métrica                   | Original           | Simplificado      |
|---------------------------|--------------------|-------------------|
| Caracteres (min–máx)      | 17 – 405           | 144 – 329         |
| Media de caracteres       | 174.3              | 239.1             |
| Mediana de caracteres     | 286                | 235               |
| Palabras (min–máx)        | 3 – 57             | 20 – 47           |
| Media de palabras         | 30.7               | 34.2              |
| Mediana de palabras       | 31                 | 33                |

---

## 4. Distribución de la puntuación de calidad

- **Media:** 0.5109
- **Mediana:** 0.8000
- **Desviación estándar:** 0.3439
- **Mínimo:** 0.0750
- **Máximo:** 0.9250

La puntuación sigue un patrón bimodal:

- **0.00 – 0.40:** oraciones complejizadas.
- **0.40 – 0.60:** simplificaciones leves.
- **0.60 – 0.75:** simplificaciones moderadas.
- **0.75 – 1.00:** simplificaciones de alta calidad.

---

## 5. Tipología de los pares

- **100 pares técnicos/científicos:** medicina, IA, biotecnología, física, etc., simplificados para código bajo escolar.
- **100 pares de textos cotidianos:** oraciones sencillas complejizadas con léxico formal o poético.

---

## 6. Criterios de construcción y refinamiento

1. **Selección de muestra:**  
   - Estratificada por dominio (técnico vs. cotidiano).  
   - Semilla de muestreo: `42`.
2. **Refinamiento con LLM:**  
   - Modelo: Claude Sonnet 4.1.  
   - Procesos en lotes de 500 pares.  
   - Validación preliminar automática y revisión humana de un 5%.  
3. **Valoración de calidad:**  
   - Puntuaciones calculadas con métricas SARI, BLEU, BERTScore, INFLESZ, LIX.  
   - Combinación en índice ponderado y normalización entre 0 y 1.  
   - Redondeo a 4 decimales.

---

## 7. Implicaciones de uso

- **Entrenamiento supervisado:** abarcar desde complicación hasta simplificación convencional.
- **Benchmark de métricas:** validación de SARI, BLEU, BERTScore, INFLESZ, LIX.
- **Análisis de estilo:** correlación entre longitud, complejidad léxica y puntuaciones humanas.
- **Pruebas de robustez:** extremos de la tarea (simplificación vs. complicación).

---

*Este README está diseñado para acompañar al archivo `Corpus_RSPSB-200.csv` y servir como guía de referencia para su utilización en proyectos de simplificación automática de texto.*

