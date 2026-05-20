<<<<<<< HEAD
# Raster to Zarr Conversion & Validation

## 📌 Overview

This guide describes the process for:

- Converting raster datasets (GeoTIFF, JP2, etc.) into Zarr format for scalable cloud storage and processing.
- Validating the generated Zarr datasets to ensure integrity and usability in the data lake.

---

## 📂 Why Zarr?

We use Zarr because:

- It stores data in chunks with compression — enabling fast partial reads.

- It is cloud-native — optimized for S3/HTTP access.

- It integrates with Xarray/Dask for parallel processing.

- It supports multi-dimensional datasets (bands × time × space).

---

## ⚙️ Conversion Process

### Input Requirements

- Input raster must be in a supported format (.tif, .tiff, .jp2).

- Ensure raster has:
  - Correct CRS (Coordinate Reference System)

  - Valid bounds

  - Clean metadata (no corrupt tags)

### Recommended Chunk Sizes

| Resolution  | Chunk Size (x, y) | Reason                                 |
|-------------|-------------------|----------------------------------------|
| `10m`       | 1024 × 1024       | Balances read performance & file count |
| `3m`        | 2048 × 2048       | Fewer chunks, faster cloud reads       |

---


## 🛠 Validation Process

After conversion, validate the Zarr dataset before ingestion into the data lake.

### Validation Steps

1. Open Zarr
2. Check Variables
3. Check Metadata
4. Check Shape & Coordinates
5. Compare with Original TIFF
6. Optional: Plot Sample Band

---

## ✅ Success Criteria

A Zarr dataset is ready for ingestion when:

- Opens without errors via xr.open_zarr.

- Contains expected variables and metadata.

- Matches dimensions and CRS of the original raster.

- Min/max values are within expected range.

- Sample plots look correct (no shifted or flipped data).

---

## 🧑‍💻 Authors & Maintainers

- Main Contributor: *Namra Mahad*
- Maintained by: *Namra Mahad (Farmdar)*
- Contact: *namra@farmdar.co.uk*
=======
# data_management
>>>>>>> fa749d0c3e74989204414d1b8718d2f8941444e6
