# Proyecto de Análisis de Sentimiento

Reseñas de Restaurantes usando Procesamiento de Lenguaje Natural (PLN)



## Título y descripción

**Nombre del proyecto:**
Proyecto de análisis de sentimiento aplicado a reseñas de restaurantes usando técnicas de PLN.



**Objetivo general:**
Desarrollar y evaluar un modelo de clasificación de texto que permita identificar el sentimiento de opiniones escritas en español.



**Contexto general:**
Este proyecto desarrolla un modelo de aprendizaje automático para clasificar opiniones de clientes en categorías de sentimiento (positivo, negativo o neutral), utilizando técnicas de procesamiento de lenguaje natural.



**Enfoque de Inteligencia Artificial:**

• *Tipo de aprendizaje:* Supervisado
• *Dominio:* Procesamiento de Lenguaje Natural (PLN)
• *Modelo base:* Modelo preentrenado de análisis de sentimiento
• *Ajuste adicional:* Fine-tuning condicional, aplicado solo si las métricas obtenidas no alcanzan un umbral mínimo de desempeño



## Tecnologías utilizadas

**Lenguaje de programación:**
• Python 3.12.12



**Librerías principales:**
• Pandas 2.2.2,
• Transformers (Hugging Face)
• Scikit-learn
• Datasets (Hugging Face)



**Herramientas de desarrollo:**
• Google Colab
• GPU NVIDIA T4
• Hugging Face Hub



## Estructura del proyecto

La siguiente estructura permite separar datos, código, modelos y resultados, facilitando la comprensión y mantenimiento del proyecto.



├─ data/		# Conjunto de datos (originales y procesados)
├─ notebooks/		# Análisis exploratorio y experimentos
├─ src/			# Código fuente (entrenamiento y predicción)
├─ models/		# Modelos entrenados y serializados
├─ results/		# Métricas, gráficas y salidas
├─ README.md		# Documentación del proyecto
└─ requirements.txt	# Dependencias del proyecto



## Instrucciones de uso

**Instalación de dependencias:**
 Abrir Google Colab
 Reiniciar Sesión en Colab (si aplica)
 Activar GPU
 Verificar la GPU



**Ejecución del código**
**Nota:** Las celdas deben ejecutarse en el orden indicado para garantizar la correcta carga de datos y evaluación del modelo.



 Celda 1 – Carga del dataset
 Celda 2 – Preparación de datos y modelo
 Celda 3 – Inferencia y medición de tiempo
 Celda 4 – Normalización de etiquetas
 Celda 5 – Evaluación del modelo
 Celda 6 – Preparación para fine-tuning (solo si es necesario - Parte 1 de 2)
 Celda 7 – Fine-tuning del modelo (solo si es necesario - Parte 2 de 2)



**Limitaciones del Proyecto**
• El dataset utilizado es **simulado**, lo que puede limitar la generalización de los resultados.
• Se emplea un **modelo preentrenado**, cuyo desempeño depende de los datos originales con los que fue entrenado.
• La evaluación se basa en métricas globales (**Accuracy y F1-score**).
• La ejecución depende del entorno **Google Colab con acceso a GPU**, lo que restringe la portabilidad y reproducibilidad en entornos locales sin ajustes adicionales.



## Resultados obtenidos

**Métricas utilizadas:**
• Accuracy
• Precision
• Recall
• F1 score



**Análisis de resultados**
• **Accuracy (0.77):** El 77 % de las opiniones fueron clasificadas correctamente, indicando un desempeño global adecuado.
• **Precision (0.83):** El modelo presenta alta confiabilidad al asignar clases de sentimiento.
• **Recall (0.77):** Se identifican correctamente la mayoría de los casos reales, aunque algunos se omiten.
• **F1-score (0.68):** Muestra margen de mejora en el equilibrio entre precisión y cobertura, especialmente en clases menos representadas.

En conjunto, estos resultados confirman que el modelo es **funcional y útil para análisis exploratorio**, aunque podría beneficiarse de ajustes adicionales mediante **fine-tuning**, particularmente si se requiere una detección más precisa de opiniones críticas.

Estos resultados permiten cumplir el objetivo general del proyecto, validando la viabilidad del uso de técnicas de PLN para el análisis de sentimiento en reseñas de restaurantes.



## Créditos

**Autor:** Guillermo Ambriz Carreon
**Empresa:** Universidad Tecmilenio
**Certificado:** Gestión de proyectos de inteligencia artificial
**Fecha:** Diciembre 2025



## Licencia

Proyecto desarrollado **exclusivamente** con fines académicos.

