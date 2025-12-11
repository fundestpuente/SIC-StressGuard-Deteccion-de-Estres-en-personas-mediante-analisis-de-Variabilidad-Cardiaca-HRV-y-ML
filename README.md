# 📌 StressGuard: Sistema Multimodal de Detección Temprana de Estrés mediante Fusión de Sensores Wearables e Inteligencia Artificial.
Curso: Samsung Innovation Campus – Módulo de Python (Ecuador 2025)
Seccion: EC03
Grupo: 01
Carpeta: /EC03/SIC-STRESSGUARD-DETECCION-DE-ESTRES-EN-PERSONAS-MEDIANTE-ANALISIS-DE-VARIABILIDAD-CARDIACA-HRV-Y-ML

Integrantes del Grupo
- Kevin Perez
- Alejandro Obando
- Danna Ayala
- Valentina Cañizares
- Daniela Mata

Descripción del Proyecto
    El estrés crónico es considerado por la Organización Mundial de la Salud (OMS) como una "epidemia de salud mundial del siglo XXI". El proyecto desarrolla un sistema algorítmico de clasificación automática para identificar estados de estrés agudo a partir de datos fisiológicos objetivos recolectados por dispositivos wearables. Utiliza señales multimodales del dataset WESAD (EDA, ECG, EMG, Temperatura) y compara algoritmos como Random Forest, KNN y Decision Tree para detectar patrones de estrés, sentando las bases para una futura aplicación móvil de monitoreo en tiempo real e intervención preventiva.

## 📁 Organización de Carpetas

```
SIC-StressGuard-Deteccion-de-Estres-en-personas-mediante-analisis-de-Variabilidad-Cardiaca-HRV-y-ML/
│
├── 📄 main.py                      # Script principal de ejecución del pipeline completo
├── 📄 wesad_data.py                # Módulo de carga y caché de datos del dataset WESAD
├── 📓 StressGuard.ipynb            # Notebook interactivo con análisis exploratorio y modelado
├── 📄 requirements.txt             # Dependencias del proyecto
├── 📄 README.md                    # Documentación del proyecto
├── 📄 tempCodeRunnerFile.py        # Archivo temporal generado por Code Runner
├── 📄 .gitignore                   # Archivos y carpetas ignoradas por Git
│
├── 📂 src/                         # Código fuente modular del proyecto
│   ├── __init__.py                 # Inicializador del paquete src
│   ├── pre_processing.py           # Preprocesamiento de datos (split, imputación, escalado)
│   ├── modelado_regularizado.py    # Entrenamiento y evaluación de modelos ML tradicionales
│   ├── graficos.py                 # Generación de gráficos de rendimiento y ROC curves
│   └── intervalos.py               # Análisis de intervalos de confianza y visualizaciones
│
├── 📂 Deep_Learning/               # Módulo de modelos de Deep Learning
│   ├── __init__.py                 # Inicializador del paquete Deep_Learning
│   └── deep_models.py              # Implementación de modelos profundos (TabNet, XGBoost)
│
└── 📂 img/                         # Resultados visuales generados automáticamente
    ├── modelos/                    # Gráficos comparativos de rendimiento entre modelos
    ├── intervalos/                 # Visualizaciones de intervalos de confianza
    └── deep/                       # Gráficos de modelos de Deep Learning
```

### 📋 Descripción de Módulos Principales

#### **`main.py`**
- Punto de entrada principal del sistema
- Orquesta el pipeline completo: carga de datos → preprocesamiento → modelado → evaluación → visualización
- Configurable mediante variables: `TEST_SUBJECTS`, `QUICK_MODE`, `USE_CROSS_VALIDATION`

#### **`wesad_data.py`**
- Descarga y carga del dataset WESAD desde Kaggle
- Procesamiento de archivos pickle por sujeto (S2-S17)
- Remuestreo de señales a 700 Hz
- Sistema de caché para optimizar tiempos de carga

#### **`src/pre_processing.py`**
- Split estratégico por sujeto (Leave-Subject-Out)
- Imputación de valores faltantes
- Escalado de características (StandardScaler)
- Verificación anti-leakage entre train y test

#### **`src/modelado_regularizado.py`**
- Implementación de modelos ML: Random Forest, XGBoost, KNN, Decision Tree, SVM, Naive Bayes
- Hiperparámetros optimizados anti-sobreajuste
- Manejo de desbalanceo de clases
- Validación cruzada opcional (GroupKFold)
- Métricas: Accuracy, Precision, Recall, F1-Score, ROC-AUC

#### **`src/graficos.py`**
- Generación de gráficos comparativos entre modelos
- Curvas ROC con AUC
- Matrices de confusión
- Guardado automático con timestamp

#### **`src/intervalos.py`**
- Análisis estadístico de intervalos de confianza
- Visualizaciones de distribuciones de métricas
- Comparación de rendimiento entre modelos

#### **`Deep_Learning/deep_models.py`**
- Modelos de Deep Learning: TabNet, XGBoost optimizado
- Entrenamiento con early stopping
- Visualizaciones específicas para modelos profundos
- Comparación con modelos tradicionales

Instrucciones de Instalación y Ejecución
- Requisitos
- Python 3.9+ (recomendado)
- Git
- Pasos
- Clonar el repositorio (o asegurarse de estar en la carpeta del proyecto):

git clone https://github.com/fundestpuente/SIC-StressGuard-Deteccion-de-Estres-en-personas-mediante-analisis-de-Variabilidad-Cardiaca-HRV-y-ML.git
cd '.\SIC-StressGuard-Deteccion-de-Estres-en-personas-mediante-analisis-de-Variabilidad-Cardiaca-HRV-y-ML\'
Abrir carpeta SIC-StressGuard-Deteccion-de-Estres-en-personas-mediante-analisis-de-Variabilidad-Cardiaca-HRV-y-ML

Ejecutar la aplicación: a. Abrir archivo StressGuard.ipynb. b. Se puede ejecutar por celda de forma ordenada. c. Se puede ejecutar todas las celdas con el boton en la parte superior del IDE que dice 'Run All'.

Herramientas Implementadas
- Lenguaje: Python 3.12
- Librerías principales: pandas, numpy, scipy, kagglehub
- Otras herramientas: Visual Studio Code, GitHub



## Split por Sujeto
Es una estrategia común en ML cuando trabajas con datos de personas:
Leave-Subject-Out (LSO)

Dejas algunos sujetos completamente fuera del entrenamiento
Simula predecir en personas nuevas que el modelo nunca vio
Más realista que mezclar datos del mismo sujeto en train y test

## Ventajas:
✅ Evita data leakage - Ningún dato del sujeto S16/S17 contamina el train
✅ Generalización real - Prueba si el modelo funciona con personas nuevas
✅ Más conservador - Test accuracy será más realista (puede ser menor)


## Modo de uso:
 Puede seleccionar los sujetos de su preferencia
TEST_SUBJECTS = ["S16", "S17"]

## PASOS PARA EJECUTAR
1.- En terminal ejecutar: "pip install -r requirements.txt"
2.- Ejecutar main.py 


