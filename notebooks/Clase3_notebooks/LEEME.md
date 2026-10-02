# Clase 3 · Time Series Forecasting — Notebooks anotados

Versiones anotadas en español de los notebooks de los capítulos 2 a 9 del repositorio
`juandata-dev/TimeSeriesForecastingInPython` (libro *Time Series Forecasting in Python*, Marco Peixeiro).
Se entregan **ya ejecutados**, con los resultados a la vista.

## Cómo instalarlos
Copia cada archivo en la carpeta del mismo nombre dentro del repositorio (por ejemplo,
`CH07/CH07_anotado.ipynb` va en `TimeSeriesForecastingInPython/CH07/`). Deben quedar ahí porque leen los datos
con la ruta relativa `../data/`.

## Qué se usa en clase
| Notebook | Tema | Momento de la clase |
|---|---|---|
| CH02_anotado | Baselines y MAPE | Demo 1 · Bloque 1 |
| CH03_anotado | Caminata aleatoria, estacionariedad, ADF, ACF | Demo 2 · Bloque 1 |
| CH04_anotado / CH05_anotado | MA(q) con la ACF · AR(p) con la PACF | Demo 3 (opcional) · Bloque 2 |
| CH06_anotado | ARMA, AIC, análisis de residuos | Solo para casa |
| CH07_anotado | ARIMA sobre J&J | Demo 4 · Bloque 2 |
| CH08_anotado | STL y SARIMA sobre pasajeros aéreos | Demo 5 · Bloque 3 |
| CH09_anotado | SARIMAX sobre el PIB de EE. UU. | Demo 6 · Bloque 3 |

## Cambios respecto al código original (marcados con 🛠️ en cada notebook)
- **Ljung-Box:** `acorr_ljungbox` devuelve un DataFrame en statsmodels reciente; el código original imprimía solo el texto `lb_pvalue`.
- **pandas 2.x/3.x:** la asignación encadenada `df['col'][a:] = …` ya no modifica el DataFrame (CH04, CH05, CH06); ahora se usa `df.loc[…]`.
- **`tqdm_notebook`** (obsoleto) reemplazado por `tqdm.auto`.
- **CH08:** `np.diff(x, n=12)` no es una diferencia estacional (es una diferencia de orden 12). Se conserva la celda original y se agrega la correcta (`x[12:] - x[:-12]`). También se corrige un gráfico que usaba una variable del capítulo 7.
- **CH09:** celda 🔬 extra que explica que `get_prediction(exog=exog)` devuelve una predicción dentro de la muestra y muestra el pronóstico con `get_forecast`, junto con la advertencia sobre la fuga de información.
- **Búsquedas en malla lentas** (CH06, CH08, CH09): desactivadas con `EJECUTAR_BUSQUEDA = False`; muestran el resultado conocido del libro. Cambia a `True` para correrlas completas (pueden tardar más de 15 minutos).

Probados con Python 3.11, pandas 3.0, numpy 2.4 y statsmodels 0.15: los 8 notebooks corren de principio a fin sin errores.
