# CONUS404 Zarr Changelog

This changelog documents major changes to the [CONUS404 zarr datasets](./CONUS404_ACCESS.md). We do not anticipate regular changes to the dataset, but we may need to fix an occasional bug or update the dataset with additional years of data. Therefore, we recommend that users of the CONUS404 zarr data check this changelog regularly.

## 2023-11
Removed derived variables (E2, ES2, RH2, SH2) that were not part of original CONUS404 model output from CONUS404 zarr stores `conus404-hourly-*`, `conus404-daily-*`, `conus404-monthly-*`.