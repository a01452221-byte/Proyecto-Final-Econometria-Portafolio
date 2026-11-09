# Proyecto final de Econometría: portafolio de 10 acciones

**Autor:** Marco Antonio Acevedo Mendoza, Maestría en Finanzas, EGADE Business School (Tecnológico de Monterrey)

Modelos econométricos aplicados a 10 acciones (MU, AMD, META, VST, CEG, FSLR, HCA, ABNB, LLY y JPM), con SPY, QQQ y el VIX como variables de mercado. Con los resultados se diseñó una operación simulada en **HowMarketsWorks**: compra en la apertura y venta antes del cierre del lunes 9 de noviembre de 2026. Guía teórica: Gujarati y Porter, *Econometría*, 5.ª ed.

## Contenido

| Archivo | Descripción |
|---|---|
| `proyecto_final_econometria.Rmd` | Código en R Markdown con todos los modelos |
| `proyecto_final_econometria.html` | Cuaderno ejecutado con resultados, tablas y gráficas (descárgalo y ábrelo en el navegador) |
| `Resumen_ejecutivo_proyecto_final.docx` | Resumen ejecutivo: resultados y justificación de las compras |
| `datos/` | 49 archivos de LSEG Workspace (Refinitiv) |

## Modelos

1. **Regresión lineal simple:** modelo de mercado (beta) contra el S&P 500 a 5 min, 30 min y diario, con errores Newey-West.
2. **Regresión lineal múltiple:** mercado, factor tecnología (QQQ − SPY), cambio del VIX y dummies de eventos y horario. Diagnóstico con VIF, Breusch-Pagan, Durbin-Watson y pruebas F.
3. **Datos de panel:** rendimiento trimestral contra fundamentales (cambio del EPS, crecimiento de ingresos, margen, deuda, tamaño). MCO agrupado, efectos fijos, de dos vías y aleatorios, con pruebas F, Breusch-Pagan LM y Hausman.
4. **Series de tiempo:** ADF y ARIMA (Box-Jenkins) con validación fuera de muestra y pronóstico.
5. **GARCH(1,1)-t y GJR-GARCH:** volatilidad diaria, de 30 min y de apertura a cierre.
6. **Portafolio:** pesos iguales, mínima varianza y máximo Sharpe, VaR 95% y órdenes de compra.

## Datos (`datos/`)

| Tipo | Archivos | Periodo |
|---|---|---|
| Precios de 5 min | `TICKER_5min.xlsx` (13) | 5 oct - 6 nov 2026 |
| Precios de 30 min | `TICKER_30min.xlsx` (13) | may - nov 2026 |
| Precios diarios | `TICKER_daily.xlsx` (13) | 2020 - nov 2026 |
| Estados financieros trimestrales | `TICKER_trimestral.xlsx` (10) | 2021 - 2026 |

## Cómo reproducirlo

1. Clona o descarga el repositorio.
2. Abre `proyecto_final_econometria.Rmd` en RStudio (R ≥ 4.2). El parámetro `DIR_DATOS` ya apunta a la carpeta `datos`.
3. Instala los paquetes que falten:
   ```r
   install.packages(c("readxl", "dplyr", "tidyr", "purrr", "stringr", "lubridate", "zoo", "xts",
                      "ggplot2", "lmtest", "sandwich", "car", "plm", "tseries", "forecast",
                      "rugarch", "FinTS", "quadprog"))
   ```
4. Presiona **Knit** para generar el HTML o el Word.

> Ejercicio académico con dinero simulado. Ningún resultado es una recomendación de inversión.
