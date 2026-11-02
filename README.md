# Satellite and Radar Mini Project

Analysis of atmospheric aerosol optical depth (AOD at 550 nm) by species, 2020–2024, using gridded reanalysis data in Python.

## What the notebook does
- Loads `aerosols_species.nc` with xarray
- Extracts five aerosol species: black carbon, dust, organic matter, sea salt, sulphate
- Computes monthly means and area-averaged time series
- Produces summary statistics (mean, max, min, standard deviation)
- Computes seasonal means and plots them as bar charts
- Maps spatial patterns with Cartopy

## Requirements
```
pip install -r requirements.txt
```

## Data
The NetCDF file `aerosols_species.nc` is not included in this repository (file size). Place it in the same folder as the notebook before running.

## Run
```
jupyter notebook Satellite_and_radar_mini_project.ipynb
```
