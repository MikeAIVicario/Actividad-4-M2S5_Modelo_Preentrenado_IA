# IA-HAR

Las metodologías tradicionales de medición y conciliación volumétrica en tanques (estática), patines de medición e instalaciones de separación (dinámica) operan con desfases temporales (batching), dependencia de registros manuales y margen de error por variaciones termo-fisicoquímicas no capturadas a tiempo. 

Además, que el sector de hidrocarburos en México a través del Servicio de Administración Tributaria (SAT) exige que las empresas de hidrocarburos cumplan con estrictos lineamientos de medición, registro, conciliación y trazabilidad de volúmenes en todas las etapas de la cadena: extracción, transporte, almacenamiento y comercialización.

Debido a que hay varias problemáticas que se requieren atender es posible proponer, más allá de una única solución, una plataforma digital integral constituida por módulos. En tal sentido se hablará del IA-HAR (Artifitial Intelligence to Hydrocarbon Accounting & Reconciliation). 

AI HAR es una iniciativa estratégica diseñada para transformar la gestión volumétrica y la integridad fiscal en operaciones de hidrocarburos mediante el uso de Inteligencia Artificial Multimodal, cumpliendo de forma estricta los lineamientos del SAT (Anexo 30/31). El proyecto responde a una necesidad crítica del sector: garantizar mediciones confiables, trazabilidad completa y conciliaciones automáticas que eliminen riesgos fiscales, operativos y reputacionales a través de: 



## Título y descripción

**Nombre del proyecto:**
IA-HAR (Artifitial Intelligence to Hydrocarbon Accounting & Reconciliation). 

**Objetivo general:**
Desarrollar y evaluar modelos que permitan:
Modelos de Machine Learning para detección de anomalías volumétricas (fugas, desviaciones, pérdidas no técnicas).
IA generativa para conciliación automática de reportes SAT, generando explicaciones y trazabilidad de cada ajuste.
Vision Computacional para validar lecturas de instrumentos (medidores, manómetros, indicadores analógicos).


**Contexto general:**
Los instrumentos normativos clave son:
•	Anexo 30 – Estándares de medición y control volumétrico Establece cómo deben capturarse, transmitirse y resguardarse los datos de medición (caudal, presión, temperatura, densidad, factor de corrección, etc.).
•	Anexo 31 – Reportes electrónicos y trazabilidad fiscal Define los formatos XML, periodicidad, validaciones y auditorías para garantizar integridad fiscal y evitar pérdidas no técnicas.


**Enfoque de Inteligencia Artificial:**

1. Detección de Anomalías Volumétricas (distilbert-base-uncased)
	Criterio Técnico: Arquitectura basada en Transformers livianos (38% menos parámetros que BERT original) optimizada para inferencia ultrarrápida.
	Justificación Operativa: En el monitoreo de flujos y presiones en ductos o tanques, el volumen de datos de telemetría es masivo. Se priorizó una baja latencia en GPU para detectar desviaciones o fugas en tiempo real sin saturar los recursos de cómputo.

2. Conciliación y Auditoría Fiscal SAT (google/flan-t5-base)
	Criterio Técnico: Modelo Encoder-Decoder ajustado por instrucciones (Instruction-tuned LLM), especializado en razonamiento, síntesis y seguimiento de reglas complejas en texto.
	Justificación Operativa: La conciliación volumétrica requiere auditar discrepancias entre reportes contables y normativas del SAT. Se seleccionó por su capacidad para generar explicaciones legibles, trazables y clasificar inconformidades, sacrificando latencia en favor de interpretabilidad y precisión conceptual.


3. Validación Visual de Instrumentos (google/vit-base-patch16-224)
	Criterio Técnico: Modelo de Vision Transformer (ViT) de última generación que segmenta la imagen en parches de 16x16 píxeles, superando a las CNNs tradicionales en captura de contexto global.
Justificación Operativa: En la validación de manómetros, medidores e indicadores analógicos en campo, se requiere alta robustez ante cambios de iluminación o textura. Se eligió por su alto desempeño (F1"-score" ) en tareas de clasificación y verificación visual con tiempos de procesamiento viables para inspecciones en borde.



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
Eficiencia en Tiempo Real (Detección de Anomalías / DistilBERT):

Latencia: Muestra la latencia más baja (aprox 10 a 25 ms por muestra en GPU).
Justificación: Ideal para sistemas SCADA de monitoreo continuo en tiempo real, donde procesar miles de registros por segundo es primordial para cerrar válvulas ante sospecha de fuga.
Alta Capacidad Explicativa (IA Generativa / Flan-T5):

Latencia: Registra la mayor latencia ( aprox. 150 a 300 ms por prompt).
Justificación: Aunque requiere un costo computacional más elevado, se justifica plenamente en la conciliación fiscal y regulatoria ARES/SAT, donde la precisión, trazabilidad y generación de la explicación técnica superan la necesidad de inmediatez milimétrica.
Inferencia Visual Desplegada en Borde (Visión Computacional / ViT):

Latencia: Latencia intermedia ( aprox. 30–50 ms por imagen en GPU).
Justificación: Ofrece una tasa alta de precisión ( F1>0.94 ) para la inspección digital automatizada de medidores analógicos en campo sin necesidad de intervención manual constante.

En conjunto, estos resultados confirman que el modelo es **funcional y útil para análisis exploratorio**, aunque podría beneficiarse de ajustes adicionales mediante **fine-tuning**, particularmente si se requiere una detección más precisa de opiniones críticas.

Estos resultados permiten cumplir el objetivo general del proyecto, validando la viabilidad del uso de técnicas de PLN para el análisis de sentimiento en reseñas de restaurantes.



## Créditos

**Autor:** Miguel Angel Vicario Hernandez
**Empresa:** Universidad Tecmilenio
**Certificado:** Gestión de proyectos de inteligencia artificial
**Fecha:** Octubre 2026



## Licencia

Proyecto desarrollado **exclusivamente** con fines académicos.

