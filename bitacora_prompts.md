# Bitácora de prompts

Registro de los prompts utilizados hasta la fecha de la Entrega 1 (6 de octubre de 2026).
> Completar las fechas y agregar cualquier otro prompt que el equipo haya usado.

| # | Fecha | Herramienta | Prompt (resumen) | Resultado / decisión del equipo |
|---|-------|-------------|------------------|---------------------------------|
| 1 | [completar] | IA generativa | Generar opciones de casos de impacto reales aplicados a lógica difusa. | Se propusieron 3 opciones; el equipo eligió el **triaje médico en urgencias** porque muestra bien el manejo de la ambigüedad (zonas grises) en un problema de salud crítico. |
| 2 | [completar] | IA generativa | Redactar el documento "Spront 1": objetivo, caso realista, stack (Python, scikit-fuzzy, NumPy, Pandas, Matplotlib, Google Colab) y preguntas guía. | Texto adaptado por el equipo para el documento y la presentación. |
| 3 | [completar] | IA generativa | Elaborar un prompt para generar el prototipo del sistema de triaje difuso. | Se obtuvo el prompt del prototipo (ver #4). |
| 4 | [completar] | Claude | **Prompt del prototipo:** "Actúa como Desarrollador Senior de IA y Ciencia de Datos… genera el prototipo funcional completo en Python (Google Colab) de un Sistema Automatizado de Triaje Médico en Urgencias basado en Lógica Difusa", con 3 entradas (temperatura, presión arterial, nivel de dolor), 1 salida (prioridad de atención), funciones de pertenencia, 5–8 reglas mínimo, gráficas, función de prueba y sección teórica de auditabilidad. | Se generó el notebook `Triaje_Difuso_Prototipo.ipynb`. La IA amplió a 23 reglas, añadió explicación de reglas activadas, verificación de cobertura y evaluación por lotes. |
