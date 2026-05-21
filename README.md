# Predicción Bursátil con Machine Learning + Explicabilidad LLM

**Curso:** Inteligencia Artificial — Universidad EAFIT, 2026-1  
**Equipo:** CSM-Coders

> Sistema que predice alzas diarias significativas (>0.5%) en 10 acciones del S&P 500 usando indicadores técnicos y modelos de ML, con explicaciones en lenguaje natural generadas por un LLM (Llama-3.1 vía Groq).

---

## Descripción

Este proyecto combina Machine Learning clásico (Logistic Regression, Random Forest, XGBoost) con IA generativa (Groq API / Llama-3.1-8b) para:

1. Predecir si el precio de cierre de una acción subirá más del 0.5% al día siguiente
2. Explicar cada predicción en lenguaje natural usando valores SHAP como contexto

**Resultado principal:** AUC-ROC = 0.576 (Random Forest), superando el baseline (LR, AUC = 0.524) en +5.2 puntos porcentuales. El LLM logra 100% de coherencia en las señales generadas.

---

## Instalación y ejecución

### Opción 1: Google Colab

1. Abrir el trabajo en notebook Google Colab:  

2. Configurar la API key de Groq:
   - Panel izquierdo → llave Secrets → Add new secret
   - Name: `GROQ_API_KEY`
   - Value: tu clave de [console.groq.com/keys](https://console.groq.com/keys) 
   - Activar "Notebook access"

3. Ejecutar todas las celdas en orden (Runtime → Run all)

### Opción 2: Ejecución local

```bash
# Clonar el repositorio
git clone https://github.com/CSM-Coders/Proyecto_Final_IA.git
cd Proyecto_Final_IA

# Instalar dependencias
pip install -r requirements.txt

# Configurar API key de Groq
export GROQ_API_KEY="tu_api_key_aqui"

# Abrir el notebook
```

**Tiempo estimado de ejecución:** ~5 minutos (descarga de datos + Optuna 60 trials + 16 llamadas al LLM).

---

## Video demo

**[Ver demo (≤3 min)](https://youtu.be/qY6_h1KhLoo)**

---

## Resultados principales

| Modelo | Accuracy | F1 | AUC-ROC | MCC |
|--------|----------|-----|---------|-----|
| Baseline (Logistic Regression) | 0.636 | 0.120 | 0.524 | 0.047 |
| Random Forest (500 árboles) | 0.621 | 0.305 | **0.576** | 0.086 |
| XGBoost + Optuna (60 trials) | 0.644 | 0.032 | 0.570 | 0.052 |

**Evaluación del LLM (15 casos de prueba):**
- Coherencia de señal: 100%
- Factores SHAP mencionados: 1.7/3 promedio
- Mención de riesgos: 67%

---

## Stack técnico

- **Datos:** Yahoo Finance (`yfinance`)
- **ML:** scikit-learn, XGBoost, Optuna
- **Explicabilidad:** SHAP
- **LLM:** Groq API (Llama-3.1-8b-instant) — gratuito
- **Visualización:** matplotlib, seaborn
- **Informe:** LaTeX (Overleaf)

---

## Equipo

| Integrante | Correo | Contribución |
|-----------|--------|-------------|
| Camilo Alvarez | calvarezv1@eafit.edu.co | EDA, preprocesamiento, feature engineering |
| Matias Monsalve | mmonsalvr1@eafit.edu.co | Modelado ML, tuning Optuna, evaluación |
| Samuel Calderon | sscalderod@eafit.edu.co | SHAP, integración LLM (Groq), prompts |

