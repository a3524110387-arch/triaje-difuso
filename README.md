# Sistema de Triaje Médico en Urgencias con Lógica Difusa

**Entrega 1 – Prototipo funcional y repositorio** · Fecha de entrega: 6 de octubre de 2026
**Integrantes:** [completar nombres del equipo] · **Repositorio:** [completar URL de GitHub/GitLab/carpeta compartida]

> ⚠️ Prototipo académico con datos simulados. No sustituye el criterio médico ni debe usarse con pacientes reales.

## 1. Problemática a resolver
Las computadoras tradicionales deciden con límites binarios: con 38.0 °C el paciente pasa a urgencias y con 37.9 °C va a la sala de espera general. En un contexto médico, una diferencia de décimas no justifica un trato opuesto. Se necesita un sistema que evalúe los signos vitales de forma **gradual** y que explique su decisión.

## 2. Descripción del proyecto
Prototipo en Python (Google Colab) que recibe tres signos vitales —temperatura, presión arterial sistólica y nivel de dolor— y calcula una **prioridad de atención de 0 a 100** mediante un sistema de inferencia difuso tipo Mamdani. Incluye 23 reglas `SI … Y … ENTONCES …`, gráficas de funciones de pertenencia, el resultado defuzzificado, la lista de reglas activadas y una evaluación por lotes con datos simulados.

## 3. Rama de IA
**Lógica difusa** (sistemas basados en reglas con razonamiento aproximado). Se eligió porque maneja las "zonas grises" y es **auditable**: cada decisión se explica con las reglas que la produjeron, a diferencia de las redes neuronales tipo "caja negra".

## 4. Caso de uso
Una enfermera de triaje ingresa temperatura, presión y dolor de un paciente que llega a urgencias. El sistema devuelve la prioridad numérica, su interpretación (baja, media-baja, media-alta o crítica) y las reglas que justifican el resultado. *Ejemplo:* temp = 38.2 °C, presión = 135 mmHg, dolor = 6 → prioridad ≈ 63 (media-alta).

## 5. Requisitos
- Python 3.10+ (o Google Colab, sin instalación local).
- Librerías (ver `requirements.txt`): scikit-fuzzy, NumPy, pandas, Matplotlib (+ SciPy y NetworkX, dependencias de scikit-fuzzy).

## 6. Instalación y ejecución
**Opción A – Google Colab (recomendada)**
1. Subir `Triaje_Difuso_Prototipo.ipynb` a Colab (o abrirlo desde GitHub: *Archivo → Abrir cuaderno → GitHub*).
2. *Entorno de ejecución → Ejecutar todo*. La primera celda instala `scikit-fuzzy`.

**Opción B – Local**
```bash
git clone [URL-del-repositorio]
cd [carpeta]
python -m venv .venv && source .venv/bin/activate   # en Windows: .venv\Scripts\activate
pip install -r requirements.txt jupyter
jupyter notebook Triaje_Difuso_Prototipo.ipynb
```
Para probar un caso propio, edita la última celda: `triar_paciente(temperatura=39.1, presion_arterial=95, nivel_dolor=7)`.

## 7. Estructura del repositorio
```
├── Triaje_Difuso_Prototipo.ipynb   # código completo del prototipo
├── requirements.txt                # dependencias con versión
├── datos_prueba.csv                # 12 pacientes simulados
├── bitacora_prompts.md             # registro de prompts
└── README.md                       # este documento
```

## 8. Datos de prueba
`datos_prueba.csv` contiene 12 casos **simulados** (columnas: `id, temperatura, presion_arterial, nivel_dolor`) que cubren casos bajos, intermedios, críticos y cercanos al umbral de 38.0 °C. Si el archivo falta, el notebook lo genera.

## 9. Control de versiones
El historial de commits debe mostrar el trabajo de **todos** los integrantes. Se recomienda que cada persona haga sus propios commits (por ejemplo, por rama o por tarea) y que el equipo registre aquí quién hizo qué: [completar].

## 10. Créditos y licencias
- **Librerías:** scikit-fuzzy (BSD-3-Clause), NumPy (BSD), pandas (BSD-3-Clause), Matplotlib (licencia tipo PSF). Entorno: Google Colab.
- **Fuentes conceptuales:** teoría de conjuntos difusos (L. A. Zadeh, 1965) e inferencia tipo Mamdani (Mamdani & Assilian, 1975). Documentación de scikit-fuzzy: https://pythonhosted.org/scikit-fuzzy/
- **Datos:** simulados por el equipo; no provienen de pacientes reales. Los rangos y reglas son ilustrativos.
- **Licencia del proyecto:** [completar, p. ej. MIT].

### Declaración de uso de IA
- **Generado por IA (Claude):** la estructura inicial del notebook, las funciones de pertenencia, el conjunto de 23 reglas, el motor de inferencia, las gráficas, la función `triar_paciente()`, los datos de prueba y el borrador de este README.
- **Elegido/modificado por el equipo:** [completar: p. ej. selección del caso de uso, ajuste de rangos y reglas, revisión del código, pruebas en Colab].
- El código fue ejecutado de principio a fin con `scikit-fuzzy 0.5.0` (la versión de `requirements.txt`). [completar: confirmar que el equipo también lo ejecutó en Google Colab o en VS Code].

## 11. Limitaciones
- La defuzzificación por centroide puede "diluir" casos extremos cuando varias reglas de distinta severidad se activan a la vez.
- Los umbrales clínicos son ilustrativos; requerirían validación médica.
- Trabajo futuro: afinar reglas con datos reales (ANFIS / neuro-difuso) y añadir más signos vitales (frecuencia cardiaca, saturación de oxígeno).
