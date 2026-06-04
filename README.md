# Análisis de Series de Tiempo — Demanda Eléctrica Colombia

Análisis completo de la demanda eléctrica del Sistema Interconectado Nacional (SIN) de Colombia para el período 2015–2023, aplicando técnicas de series de tiempo sobre datos horarios reales obtenidos de la API pública de XM.

---

## Información académica

| | |
|---|---|
| **Universidad** | Universidad Tecnológica de Bolívar |
| **Programa** | Maestría en Ingeniería de Sistemas y Computación |
| **Asignatura** | Series de Tiempo |
| **Docente** | PhD. Mauro A. Maza Chamorro |
| **Estudiantes** | Jeison David Jiménez · Dayana Hurtado · Isis Orika Hernández |

---

## Datos

| Variable | Fuente | Unidad | Resolución |
|---|---|---|---|
| Demanda real del SIN | API SiMEM — XM (`dataset c1b851`) | GWh | Horaria |
| Precio de bolsa nacional | API SINERGOX — XM (`PrecBolsNaci`) | COP/kWh | Horaria |

- **Período:** 2015-01-01 al 2023-12-31
- **Total de registros:** 78 888 horas por variable
- **Cobertura:** 100%

Los datos se descargan automáticamente al ejecutar el notebook y se almacenan en `datos_xm/` para evitar llamadas repetidas a la API.

---

## Contenido del análisis

| Sección | Descripción |
|---|---|
| 1. Configuración | Dependencias, constantes y parámetros globales |
| 2. Adquisición de datos | Descarga desde APIs XM con caché local |
| 3. Análisis exploratorio | Serie diaria, perfil horario, heatmap año-mes |
| 4. Estacionariedad | Tests ADF y KPSS, diferenciación regular y estacional |
| 5. ACF y PACF | Autocorrelación, correlación parcial y correlación cruzada demanda-precio |
| 6. Análisis de Fourier | Espectro de amplitud FFT, top-20 componentes y reconstrucción progresiva |
| 7. Densidad espectral (PSD) | Método de Welch, comparación entre períodos estructurales |
| 8. Análisis crossespectral | Coherencia espectral y espectro de fase demanda-precio |
| 9. Transformada Wavelet (CWT) | Escalograma y espectro global con wavelet Morlet compleja |
| 10. Análisis de armónicos | Identificación y reconstrucción de armónicos del ciclo diario |

---

## Eventos estructurales analizados

- **El Niño 2015–2016** (abr 2015 – may 2016)
- **COVID-19** (mar 2020 – ago 2020)
- **El Niño 2023** (ene 2023 – dic 2023)

---

## Requisitos

Python 3.10+

```bash
pip install -r requirements.txt
```

---

## Ejecución

```bash
jupyter notebook demanda_electrica_colombia.ipynb
```

Ejecutar todas las celdas en orden (`Kernel → Restart & Run All`). La primera ejecución descarga los datos desde la API XM y los guarda en `datos_xm/`. Las ejecuciones siguientes cargan desde caché.

---

## Estructura del proyecto

```
colombia-electricity-demand-timeseries/
│
├── demanda_electrica_colombia.ipynb   # Notebook principal
├── requirements.txt                   # Dependencias
├── README.md
└── datos_xm/
    ├── demanda_gwh.csv                # Demanda horaria 2015-2023
    └── precio_kwh.csv                 # Precio de bolsa 2015-2023
```
