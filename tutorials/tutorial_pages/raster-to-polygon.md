---
layout: post
title:  "Convert a Raster to a Polygon"
date:   2016-03-11 8:49:00
comments: true
---



## Using GDAL and Shapely in Python

```python
#!/usr/bin/env python

# Convert Raster to Polygon
#
# B -- C
# |    |
# A -- D

import math
import gdal
import shapely


def get_position(a, b, c, d, e, f, cols, rows):
    x = a * cols - b * rows + c
    y = -d * cols + e * rows + f
    return x, y

def get_bounding_box(filepath):
    dataset = gdal.Open(filepath)
    c, a, b, f, d, e = dataset.GetGeoTransform()
    n_cols = dataset.RasterXSize
    n_rows = dataset.RasterYSize

    # Find corners of image
    bot_left = A = get_position(a, b, c, d, e, f, 0, 0)
    top_left = B = get_position(a, b, c, d, e, f, 0, n_rows)
    top_right = C = get_position(a, b, c, d, e, f, n_cols, n_rows)
    bot_right = D = get_position(a, b, c, d, e, f, n_cols, 0)

    return bot_left, top_left, top_right, bot_right

poly = shapely.geometry.Polygon(get_bounding_box(raster_filepath))
```
