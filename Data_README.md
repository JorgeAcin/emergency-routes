# Data Directory

This folder contains additional datasets used by the system. 

The 7 road restriction scenario CSVs are too large for GitHub's file size limits and are available for download in the [**Releases**](../../releases) section of this repository (`escenarios.zip`). Extract the zip to access the individual files. Each CSV encodes road closure polygons for a specific scenario, with coordinates in EPSG:25830 (UTM zone 30N) that the system automatically reprojects to WGS84.

## Available Scenarios (download from [Releases](../../releases))

| File | Scenario | Source | Records |
|------|----------|--------|---------|
| `calles_cortadas_DANA.csv` | DANA flood (Oct 29, 2024) | Generalitat Valenciana water footprints + OSM | ~55 KB |
| `calles_fallas.csv` | Fallas de Valencia | Valencia City Council shapefile | ~146 KB |
| `calles_riesgo_extremo_PATRICOVA.csv` | PATRICOVA extreme risk (levels 1-2) | GVA PATRICOVA plan | ~82 KB |
| `maraton_valencia.csv` | Valencia Marathon route | Official route + OSM intersection | ~10 KB |
| `ofrenda_fallas.csv` | Ofrenda de Fallas procession | Official route + OSM intersection | ~373 KB |
| `procesion_Sant_Vicent.csv` | San Vicente Ferrer procession | Official route + OSM intersection | ~235 KB |
| `semana_marinera.csv` | Semana Marinera processions | Official route + OSM intersection | ~306 KB |

## Confidential Files (NOT included)

The following files are **not included** in this repository because they contain confidential operational data provided by the Generalitat Valenciana:

- **`Ambulancias.csv`** — Inventory of 71 SAMU/SVB ambulance units with base locations, shift schedules, and operational details.
- **`HOSPITALES y CENTRO SALUD.csv`** — Directory of 18 hospital centers in the province of Valencia with coordinates and service capabilities.
- **AED data** — Automated External Defibrillator locations.

These datasets were provided by Yulia Karpova (Generalitat Valenciana) exclusively for academic use in this project.

## Other Data

- **`intensidad_total_23-25.csv`** — Traffic intensity data 2023–2025 from the Generalitat Valenciana. Collected for future ETA prediction development.
- **`llamadas_emergencia.xlsx`** — Synthetic emergency call dataset (504 records) used for triage model training. Located in `Code/`.
- **`datos_hidrograficos_chj.xlsx`** — River flow and reservoir data from the Júcar Hydrographic Confederation. Located in `Code/`.

## Construction Process

All restriction layers follow the same output format. The construction process varied:
- **Fallas**: Direct shapefile → reprojection → CSV export.
- **Marathon, Semana Marinera, San Vicente, Ofrenda**: Official route → QGIS line tracing → spatial intersection with OSM street network → buffer → CSV export.
- **DANA**: GVA water footprints → intersection with provincial street network → buffer → CSV export.
- **PATRICOVA**: Filtered to hazard levels 1 and 2 only (structural risk map, not event-specific).
