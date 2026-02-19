<div align="center">

<!-- Banner principal -->
<img src="assets/images/img.png" alt="Challenge 2 Data Science - Telecom X" width="100%"/>

<br/>

# 📡 TelecomX — Análisis de Evasión de Clientes

### *Challenge 2 · Data Science · Alura Latam + Oracle Next Education*

<br/>

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.0+-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Colab](https://img.shields.io/badge/Google%20Colab-Ready-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-22c55e?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completado-6366f1?style=for-the-badge)

</div>

---

## 📌 Tabla de Contenidos

1. [Sobre el Proyecto](#-sobre-el-proyecto)
2. [El Problema de Negocio](#-el-problema-de-negocio)
3. [Metodología ETL](#-metodología-etl)
4. [Estructura del Repositorio](#-estructura-del-repositorio)
5. [Tecnologías Utilizadas](#-tecnologías-utilizadas)
6. [Instalación y Uso](#-instalación-y-uso)
7. [Conclusiones Clave](#-conclusiones-clave)
8. [Autor](#-autor)

---

## 📝 Sobre el Proyecto

> **Telecom X** enfrenta una tasa crítica de **evasión de clientes (Churn) del 26%**, lo que representa una pérdida significativa de ingresos recurrentes.

Este proyecto forma parte del **Challenge 2 de Data Science** del programa **ONE (Oracle Next Education)** en alianza con **Alura Latam**. Como analista de datos, el objetivo es transformar datos crudos de la API oficial en inteligencia accionable para que el equipo de Ciencia de Datos pueda construir modelos predictivos de churn.

<div align="center">

| 📊 Dataset | 🔗 Fuente | 📁 Formato |
|:---:|:---:|:---:|
| TelecomX Customers | API pública GitHub | JSON anidado |

</div>

---

## 💡 El Problema de Negocio

```
¿Por qué los clientes abandonan Telecom X?
     │
     ├─► Tipo de contrato (Mes a Mes vs Anual)
     ├─► Método de pago utilizado
     ├─► Tiempo de permanencia (tenure)
     ├─► Nivel de cargos mensuales
     └─► Servicios contratados
```

---

## 🏗️ Metodología ETL

El proyecto sigue una arquitectura **ETL** dividida en 3 fases ágiles:

---

### ⚙️ Fase 1 — Extracción (Extract)

```python
url = "https://raw.githubusercontent.com/.../TelecomX_Data.json"
df = pd.json_normalize(requests.get(url).json())
```

- ✅ Carga de datos JSON desde la API oficial de Telecom X
- ✅ Normalización de estructura anidada con `pd.json_normalize()`
- ✅ Conversión a DataFrame de Pandas listo para transformación

---

### 🔧 Fase 2 — Transformación (Transform)

| Tarea | Descripción |
|-------|-------------|
| 🔍 Exploración | Inspección de tipos, nulos y duplicados |
| 🧹 Limpieza | Corrección de formatos y valores inconsistentes |
| 🏷️ Estandarización | Traducción de columnas al español para stakeholders |
| ⚙️ Feature Engineering | Creación de métrica `Cuentas_Diarias` |
| 🔢 Encoding | Conversión de `Churn` Yes/No → binario 1/0 |

```python
# Feature Engineering: costo diario por cliente
df['Cuentas_Diarias'] = (df['account.Charges.Monthly'] / 30).round(2)
```

---

### 📊 Fase 3 — Carga y Análisis (Load & Analysis)

- 📈 Análisis descriptivo estadístico completo
- 🥧 Visualización de distribución de churn (26% tasa de evasión)
- 📊 Countplots de evasión por tipo de contrato y método de pago
- 🌡️ Matriz de correlación entre variables numéricas y evasión

---

## 📁 Estructura del Repositorio

```
ChallengeTELECOM-X/
│
├── 📓 TelecomX_LATAM.ipynb        
├── 📄 README.md                     
├── 📄 LICENSE                     
│
└── 📂 assets/
    └── 📂 images/
        └── 🖼️ img.png
    banner_alura.svg
```

---

## 🛠️ Tecnologías Utilizadas

<div align="center">

| Herramienta | Uso |
|:-----------:|:----|
| 🐍 **Python 3.10+** | Lenguaje principal |
| 🐼 **Pandas** | Manipulación y análisis de datos |
| 📊 **Matplotlib** | Visualización estática |
| 🎨 **Seaborn** | Visualización estadística avanzada |
| 🌐 **Requests** | Consumo de API REST |
| ☁️ **Google Colab** | Entorno de ejecución en la nube |
| 🐙 **GitHub** | Control de versiones |

</div>

---

## 🚀 Instalación y Uso

### Opción A — Google Colab (Recomendado)

1. Abre [Google Colab](https://colab.research.google.com/)
2. Ve a `Archivo → Abrir cuaderno → GitHub`
3. Pega la URL de este repositorio
4. Selecciona `TelecomX_LATAM.ipynb`
5. Ejecuta las celdas en orden ▶️

### Opción B — Local

```bash
# 1. Clonar el repositorio
git clone https://github.com/TU_USUARIO/ChallengeTELECOM-X.git
cd ChallengeTELECOM-X

# 2. Instalar dependencias
pip install pandas matplotlib seaborn requests

# 3. Abrir el notebook
jupyter notebook TelecomX_LATAM.ipynb
```

---

## 📈 Conclusiones Clave

> **Hallazgo principal:** Los clientes con contrato **"Mes a Mes"** presentan la tasa de evasión más alta comparado con contratos anuales o bianuales.

| 🔍 Insight | 💡 Recomendación |
|-----------|-----------------|
| Correlación negativa entre `tenure` y churn | Incentivar la permanencia con beneficios por fidelidad |
| Clientes con altos cargos mensuales evaden más | Revisar la estructura de precios y ofrecer planes escalonados |
| Contratos mensuales = mayor riesgo | Implementar promociones para migrar a planes anuales |
| Métodos de pago electrónicos correlacionan con churn | Ofrecer descuentos por domiciliación bancaria |

---

## 🎓 Autor

<div align="center">

**Bernardo Adolfo Gómez Montoya**

Desarrollado con ❤️ en el marco de **Alura Latam + Oracle Next Education**

[![Alura Latam](https://img.shields.io/badge/Alura-Latam-1572B6?style=flat-square&logo=alura&logoColor=white)](https://www.aluracursos.com/)
[![Oracle ONE](https://img.shields.io/badge/Oracle-Next%20Education-F80000?style=flat-square&logo=oracle&logoColor=white)](https://www.oracle.com/lad/education/oracle-next-education/)

</div>

---

<div align="center">

📄 Este proyecto está bajo la **Licencia MIT** — ver el archivo [LICENSE](LICENSE) para más detalles.

</div>
