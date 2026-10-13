# Tarea 2: arquitecturas modernas de RNP
**Redes neuronales profundas [UCV] · Semestre I-2026**

Este repositorio contiene la resolución de la segunda tarea enfocada en el estudio matemático, diseño, experimentación y segmentación semántica de redes neuronales convolucionales modernas sobre señales, imágenes y el conjunto de datos **Oxford-IIIT Pet**.

## Resumen de la tarea

La tarea se estructura en las siguientes partes principales desarrolladas en los cuadernos del repositorio:

1. **Cuadernos de convolución de Understanding Deep Learning:**
   - **10.1 Convolución 1D:** implementación de filtros unidimensionales sobre señales temporales y audio.
   - **10.2 Propiedades de la convolución:** demostración analítica y práctica de conmutatividad y equivariancia a traslaciones.
   - **10.3 Convolución 2D:** aplicación de matrices de pesos sobre imágenes y diseño manual de filtros de bordes.
   - **10.4 Stride, dilatación y reducción:** impacto de convoluciones con salto, campos receptivos expandidos y submuestreo espacial.
   - **10.5 Red convolucional en PyTorch:** construcción, entrenamiento y evaluación de una red convolucional profunda para clasificación de dígitos en MNIST.

2. **Experimento de segmentación semántica en Oxford-IIIT Pet:**
   - Desarrollo en el cuaderno `experiment/06_CNN_Segmentation_hw.ipynb` utilizando TensorFlow y Keras.
   - Segmentación a nivel de píxel en tres clases: animal, fondo y borde de silueta.
   - Entrenamiento controlado bajo protocolo fijo de 40 épocas, lote de 32, tasa de aprendizaje de 1e-4 y semilla fija 1337.
   - Reproducción del modelo baseline con convoluciones separables en profundidad y remuestreo bilinear.
   - Diseño y evaluación de cuatro variantes de arquitectura:
     - **unet:** conexiones residuales tipo skip connections entre codificador y decodificador.
     - **transpose_strided:** convoluciones transpuestas con stride 2 para remuestreo aprendido.
     - **standard_conv:** sustitución de convoluciones separables por convoluciones estándar de 3x3.
     - **kernel5:** ampliación del tamaño del kernel a 5x5 en todo el codificador.

3. **Auditoría de calidad de datos y cuarentena:**
   - Detección automática de 23 imágenes con error de anotación humana en Oxford-IIIT Pet donde la máscara real era 100% fondo azul.
   - Aislamiento en cuarentena de los casos defectuosos fuera de entrenamiento y validación sin fuga de datos.
   - Evaluación comparativa de la capacidad de segmentación fina en bordes anatómicos frente al modelo reentrenado.

4. **Preguntas teóricas y comprensión del baseline:**
   - Cálculo manual paso a paso de convolución 2D con kernel de 2x2 y padding de ceros.
   - Justificación matemática de dimensiones de salida y análisis del sesgo inductivo de localidad y pesos compartidos.
   - Estudio del desbalance de clases, trazado de dimensiones del cuello de botella y cálculo manual de parámetros en convoluciones separables frente a estándar.

5. **Informe final en formato PDF:**
   - Redacción de un documento técnico de máximo 4 páginas cubriendo baseline reproducido, teoría, experimentos, análisis de resultados y handover.

> [!TIP]
> Para el experimento de segmentación en `experiment/06_CNN_Segmentation_hw.ipynb`, se recomienda ejecutar directamente en Google Colab con acelerador GPU T4 para completar las 40 épocas en pocos minutos por modelo.

## Configuración del entorno de ejecución

El proyecto utiliza el entorno virtual local `.venv` ubicado en la raíz del proyecto con Python 3.12.

### 1. Activar el entorno virtual
```bash
source .venv/bin/activate
```

### 2. Instalar dependencias
```bash
pip install -r requirements.txt
```

### 3. Seleccionar el kernel o entorno en Jupyter o el editor
Al abrir los cuadernos de `notebooks/` o `experiment/`:
- Seleccionar el entorno virtual de la raíz: **`.venv`** ubicado en `.venv/bin/python`.
