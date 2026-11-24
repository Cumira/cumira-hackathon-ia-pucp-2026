# Cumira · Inicio del equipo

Preparación inicial: 24 de noviembre de 2026. Repositorio creado desde la plantilla oficial de la Hackathon IA PUCP 2026.

## Estado real

Este repositorio contiene el baseline y el ejemplo originales. Todavía no se entrenó aquí un modelo propio ni se eligió el producto final. El score ~0,40 es una referencia oficial del starter.

- `train/starter_notebook.ipynb` define y entrena una CNN; hay que ejecutarlo para obtener pesos.
- Podemos modificar esa CNN o crear otro modelo. La arquitectura no es obligatoria.
- `app/ejemplo_producto.py` contiene una interpolación de relleno; todavía no usa la CNN entrenada. Debemos reemplazar `predecir()` por nuestro modelo final.
- Producto y submission final deben usar los mismos pesos y el mismo preprocesamiento.
- La carpeta `data/` no incluye los datasets: descargarlos desde Kaggle. No publicarlos.

## Qué predice la CNN

```text
GFS t−2, t−1, t (3 × 17 × 13 × 4) + hora UTC + relieve
                              ↓
           RH, T, U, V en la hora t (70 × 35 × 4)
```

Aprende anomalías sobre la climatología por hora y aproxima WRF a 3 km. El pronóstico futuro lo aporta GFS. No genera precipitación ni alertas directamente.

## Ejecutar el starter en Windows / PowerShell

Desde la raíz de este repositorio, con Python instalado:

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m notebook train/starter_notebook.ipynb
```

Antes de ejecutar sus celdas, colocar `train.npz`, `test.npz`, `static.npz` y `sample_submission.csv` en `data/`, obtenidos de la competencia. Este comando abre Jupyter; el entrenamiento se ejecuta desde el notebook. La plantilla también está preparada para Kaggle o Colab.

## Primeras tareas

- [ ] Confirmar integrantes y nombre oficial del equipo en Kaggle.
- [ ] Descargar la data oficial y ejecutar el baseline sin modificaciones.
- [ ] Registrar score local y RMSE por variable con corte temporal.
- [ ] Elegir usuario objetivo y producto.
- [ ] Comparar mejoras del baseline u otras arquitecturas.
- [ ] Exportar pesos y artefactos de normalización, climatología, escala y grilla para la inferencia. El `state_dict()` del starter no contiene todos esos valores externos.
- [ ] Integrar esos mismos artefactos y pesos con GFS actual en `app/`.
- [ ] Completar el README para el producto, `REPORTE_PRODUCTO.md`, notebook final reproducible y video.

El README oficial contiene la guía detallada. La entrega cierra el **8 de diciembre de 2026 a las 23:59, hora de Lima**. Confirmar el límite diario de envíos: las fuentes disponibles discrepan entre 5 y 10.
