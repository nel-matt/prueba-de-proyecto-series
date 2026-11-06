# Equipo 8 — Proyecto Módulo 3

Pronóstico de ventas semanales con contexto (2026-W31 a 2026-W42) para el curso
de Forecasting de Series de Tiempo (ITESO).

## Estructura

```
├── _quarto.yml
├── proyecto_m3.qmd      # todo el trabajo (presentación RevealJS)
├── proyecto_m3.html     # render del .qmd
├── datos/
│   └── ventas_semana_train.RData
└── equipo_8.RData       # pronóstico final (lo genera el .qmd)
```

## Cómo reproducir

1. Clonar el repo y abrir la carpeta en Positron.
2. Paquetes (CRAN): `fpp3`, `timeDate`, `knitr`.
3. `quarto render proyecto_m3.qmd` (sin caché; tarda unos minutos por la validación cruzada).

El render genera `proyecto_m3.html` y `equipo_8.RData` y corre `validar_entrega()`.

## Modelo final

Combinación `(ARIMA + TSLM) / 2` sobre `log(total)`, ambos con Fourier anual
(K = 8, periodo 52.18), festivos oficiales (LFT art. 74), Semana Santa y una
indicadora del evento de 2021-W43. Elegido con validación cruzada de origen
móvil (31 folds, h = 12, `.step = 4`).

Material del curso: <https://pbenavidesh.github.io/narsil>
