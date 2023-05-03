# HyTEST Intake Sub-Catalogs
This section describes how to use the subcatalogs contained in HyTEST's main data catalog (`hytest_intake_catalog.yml`). Example usage of the CONUS404 sub-catalog is shown below.

```python
import intake
hytest_cat = intake.open_catalog("https://raw.githubusercontent.com/hytest-org/hytest/main/dataset_catalog/hytest_intake_catalog.yml")
list(hytest_cat)
```

produces a list of datasets and sub-catalogs in the main HyTEST data catalog, for example:
```
['conus404-hourly-onprem',
 'conus404-hourly-cloud',
 'conus404-daily-diagnostic-onprem',
 'conus404-daily-diagnostic-cloud',
 'conus404-daily-onprem',
 'conus404-daily-cloud',
 'conus404-monthly-onprem',
 'conus404-monthly-cloud']

```
We can then open the CONUS404 sub-catalog with:
```python
cat = hytest_cat['conus404-catalog']
list(cat)
```
producing a list of all the CONUS404 dataset versions:
```
['conus404-hourly-onprem',
 'conus404-hourly-cloud',
 'conus404-hourly-osn',
 'conus404-daily-diagnostic-onprem',
 'conus404-daily-diagnostic-cloud',
 'conus404-daily-onprem',
 'conus404-daily-cloud',
 'conus404-monthly-onprem',
 'conus404-monthly-cloud']
```

The characteristics of indivdual datasets can be explored:
```python
cat['conus404-hourly-cloud']
```
producing
```yaml
conus404-hourly-cloud:
  args:
    consolidated: true
    storage_options:
      requester_pays: true
    urlpath: s3://nhgf-development/conus404/conus404_hourly_202209.zarr
  description: 'CONUS404 Hydro Variable subset, 40 years of hourly values. These files
    were created wrfout model output files (see ScienceBase data release for more
    details: https://www.sciencebase.gov/catalog/item/6372cd09d34ed907bf6c6ab1). This
    dataset is stored on AWS S3 cloud storage in a requester-pays bucket. You can
    work with this data for free if your workflow is running in the us-west-2 region,
    but you will be charged according to AWS S3 pricing (https://aws.amazon.com/s3/pricing/)
    to read the data into a workflow running outside of the cloud or in a different
    AWS cloud region.'
  driver: intake_xarray.xzarr.ZarrSource
  metadata:
    catalog_dir: https://raw.githubusercontent.com/hytest-org/hytest/main/dataset_catalog/subcatalogs
```