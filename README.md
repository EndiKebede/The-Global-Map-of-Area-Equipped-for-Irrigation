# AEI Downscaling Python Implementation

## Overview

This project implements a **pixel-level downscaling apporach for Area Equipped for Irrigation (AEI)** based on the original C++ code developed by **Stefan Siebert**. The method allocates irrigated area across agricultural pixels using stepwise logic and multiple constraints (GMIA irrigated area dataset, cropland, pasture, and land availability), now rewritten in **Python** for reproducibility and extensibility.

This Python implementation was developed by:

**Endalkachew Kebede**  
Department of Geography and Spatial Sciences  
University of Delaware  
📧 endiabe@udel.edu

---

## Original Author

The original algorithm and stepwise downscaling logic were created by **Prof. Stefan Siebert** and implemented in C++. 
This Python version retains the pixel-by-pixel logic and structure of the original method.

---

## Features

- **Supports multiple scenarios** (`base`, `low`, `upper`, `hyde_base`, `hyde_low`, `hyde_upper`)
- Step-by-step irrigation allocation (Steps 1–10) with:
  - GMIA-based constraints (Steps 1–7 run only if GMIA > 0)
  - Cropland/pasture fallback logic (Steps 8–10 run if GMIA == 0)
  - Hybrid allocation using **relative and absolute scaling**
- Per-step allocation tracking (`debug CSV` for each unit)
- Maximum allocation capped by **land availability**
- Compatible with **HYDE cropland/pasture maps**

---
<img width="1755" height="1155" alt="image" src="https://github.com/user-attachments/assets/273dd97b-80e7-4c03-9a66-a94cab28e1aa" />

## Input Data Requirements

- `GMIA` rasters for 2005
- `Cropland` and `Pasture` rasters from HYDE (5 arc-min)
- `Land availability` raster
- `Shapefiles` for subnational units (with `unit_code`)
- AEI statistics as `.xlsx` with matching `unit_code`

---

## Output

- **GeoTIFF** files for each scenario and year showing downscaled AEI (irrigated area)
- **Debug CSVs** with per-unit allocation summary:
  - Target vs allocated AEI
  - Step-by-step allocation values

---

## Usage

Set up the `base_dir` in the script to point to your data directory.

************************************************************
Contact Information

For further information, please contact:

- Endalkachew Abebe Kebede: e-mail: endiabe@udel.edu
- Kyle Frankel Davis: e-mail: kfdavis@udel.edu
