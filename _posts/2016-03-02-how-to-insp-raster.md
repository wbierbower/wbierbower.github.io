---
layout: post
title:  "Inspect the Contents of a Raster"
date:   2016-03-02 17:34:00
comments: true
---

## GDAL's `gdalinfo` Command Line Tool

Provides the following information:

- Driver Type
- Files
- Dimensions
- Coordinate System
- Metadata
- Corner Coordinates
- Band Statistics

```bash
$ gdalinfo path/to/file.tif
```

## RasterIO's `rio insp` Command Line Tool

Provides the following information:

- Affine Transform
- Coordinate System
- Band Count
- Driver Type
- Datatype
- Dimensions
- Nodata

```bash
$ pip install rasterio
$ rio insp path/to/file.tif
```

```python
>>> import pprint as pp
>>> pp.pprint(src.meta)  # raster metadata
```

## GDAL's Python Bindings

A sampling of what information this method provides:

- Geotransform
- Coordinate System
- Band Count
- Driver Type
- Dimension
- Nodata

```python
#!/usr/bin/env python
import gdal

def insp_raster(filepath):
    dataset = gdal.Open(filepath)
    driver = dataset.GetDriver()
    band = dataset.GetRasterBand(1)
    array = band.ReadAsArray()

    geotransform = dataset.GetGeoTransform()
    coord_sys = dataset.GetProjection()
    band_count = dataset.RasterCount
    driver_type = driver.GetDescription()
    dimensions = (dataset.RasterXSize, dataset.RasterYSize)
    nodata = band.GetNoDataValue()

    print 'Geotransform:', geotransform
    print 'Coordinate System:', coord_sys
    print 'Band Count', band_count
    print 'Driver Type', driver_type
    print 'Dimensions', dimensions
    print 'Nodata', nodata

    ds, driver = None, None

insp_raster('path/to/file.tif')
```
