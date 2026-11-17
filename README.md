# PM2.5, PM10 and Surface Solar Radiation Over Ghana

Analysis of how particulate matter (PM2.5 and PM10) relates to surface solar radiation (SSR) over Ghana, using CAMS air quality data and ERA5 radiation data for 2022.

**Notebook:** `PM2_5_PM10_SSR_analysis.ipynb`

## Overview

The notebook:

1. Loads a merged CAMS + ERA5 NetCDF file (hourly, 2015-2025, 0.25° grid).
2. Masks the grid to Ghana using an agro-ecological zones (AEZ) GeoJSON (309 of 609 grid points fall inside Ghana).
3. Subsets 2022 and computes Ghana-wide hourly, monthly and annual means.
4. Converts units: PM from kg/m³ to µg/m³ (×10⁹) and SSR from J/m² per hour to W/m² (÷3600).
5. Plots monthly PM2.5 and PM10 with Harmattan (Dec-Feb) and rainy-season (Apr-Oct) shading, and WHO 2021 annual guidelines (PM2.5: 5 µg/m³, PM10: 15 µg/m³).
6. Maps the annual mean spatial distribution of PM2.5, PM10 and SSR, plus the coarse fraction (PM10 − PM2.5) and the PM2.5/PM10 ratio.
7. Quantifies the PM-SSR relationship:
   - grid-cell scatter plots (annual means) with linear regression, r, R² and p-value
   - monthly scatter plots with Pearson r, Spearman ρ, a 95% confidence band and seasonal colouring
   - a correlation heatmap of PM2.5, PM10 and SSR

## Data

| Variable | Source | Coverage | Resolution |
|---|---|---|---|
| PM2.5 (`pm2p5`), PM10 (`pm10`) | CAMS (Copernicus Atmosphere Monitoring Service) | Ghana region, 4.5-11.5°N, 3.5°W-1.5°E | 0.25° |
| Surface net solar radiation (`ssr`) | ERA5 (ECMWF) | Same domain | 0.25° |

Input files expected in the working directory:

- `merged_cams_era5_data.nc` (merged CAMS + ERA5 dataset)
- `ghanaAEZ.geojson` (Ghana agro-ecological zones)

> The full NetCDF file is large (about 660 MB in memory) and is not stored in this repository. Add a download link or a data-access note here (for example CAMS Atmosphere Data Store and Copernicus Climate Data Store), or use Git LFS if you decide to host it.

## Selected results (2022, Ghana-wide monthly means)

- PM2.5 peaks in January at about 106 µg/m³ and is lowest in September at about 17 µg/m³.
- PM10 peaks in January at about 140 µg/m³.
- Particulate levels are highest in the dry Harmattan months and lowest in the rainy season.
- Monthly means are above the WHO 2021 annual guidelines in every month.

Correlation statistics (r, R², p-values) are printed on the scatter plots and heatmap produced by the notebook.

## Requirements

Python 3.10+ with:

```
xarray
netCDF4
numpy
pandas
geopandas
shapely>=2.1
matplotlib
cartopy
scipy
seaborn
```

`shapely>=2.1` is needed for `GeoSeries.union_all()`. Install with:

```bash
pip install xarray netCDF4 numpy pandas geopandas "shapely>=2.1" matplotlib cartopy scipy seaborn
```

## Usage

1. Place `merged_cams_era5_data.nc` and `ghanaAEZ.geojson` next to the notebook.
2. Open `PM2_5_PM10_SSR_analysis.ipynb` in Jupyter and run all cells.
3. Figures are saved as PNG files in the working directory, including `pm25_monthly_ghana_2022.png`, `pm10_monthly_ghana_2022.png`, `Ghana_Combined_Spatial_Distribution_2022.png`, `scatter_ssr_pm_ghana_2022.png`, `scatter_ssr_pm_monthly_ghana_2022.png` and `Ghana_correlation_simple.png`.

## Authors

Group 6: Felix Asiedu Asare, Kessewaah Asenso, Ampoma Boakye Henry, Addo Kingsford, Agyeman Laurie, Emmanuel Dortumor

## Acknowledgements

Data: Copernicus Atmosphere Monitoring Service (CAMS) and ERA5 reanalysis (ECMWF / Copernicus Climate Change Service).
