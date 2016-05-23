---
layout: post
title:  "Read a Raster Band into Memory"
date:   2016-03-02 17:31:58
comments: true
---

## Using GDAL's Python Bindings

```python
#!/usr/bin/env python
import gdal

def read_raster(filepath):
    dataset = gdal.Open(filepath)
    band = dataset.GetRasterBand(1)
    array = band.ReadAsArray()
    ds = None
    return array

a = read_raster('path/to/file.tif')
```

## Using RasterIO's `rio insp` Command Line Tool

```bash
$ pip install rasterio
$ rio insp path/to/file.tif
```

```python
>>> src.meta  # raster metadata
>>> a = src.read(1)
```
