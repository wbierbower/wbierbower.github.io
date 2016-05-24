---
layout: post
title:  "Inspect the Contents of a Vector File"
permalink: /tutorials/how-to-insp-vector.html
comments: true
---

## Using OGR's `ogrinfo` Command Line Tool

```bash
# To list layers
$ ogrinfo path/to/file.shp
```

```bash
$ ogrinfo path/to/file.shp (layer)
```

Provides the following information:

- Layer name
- Geometry type
- Feature count
- Extent
- Layer SRS WKT
- PROJCS
- Name
- OGRFeature
  - Type
  - Coordinates (WKT)

## Using Fiona's `fio insp` Command Line Tool

Provides the following information:

- geometry
  - coordinates
  - type
- id
- properties
- type

```bash
$ pip install fiona
$ fio insp path/to/file.shp
```

```python
>>> import pprint as pp
>>> pp.pprint(src.schema)  # vector metadata
```


## Using OGR's Python Bindings

Provides the following information:

- Driver Type
- Layer Count
- Coordinate System
- Layer Name
- Layer Extent
- Feature Keys
- Geometry Type
- Geometry Area

```python
#!/usr/bin/env python
import ogr

def insp_vector(filepath):
    datasource = ogr.Open(filepath)
    driver = datasource.GetDriver()
    layer = ds.GetLayerByIndex(0)
    srs = layer.GetSpatialRef()
    feature = layer.GetFeature(0)
    feature_json = feature.ExportToJson()
    geometry = feature.geometry()

    print "Driver Type:", driver.GetName()
    print "Layer Count:", datasource.GetLayerCount()
    print "Coordinate System:", srs.ExportToProj4()
    print "Layer Name:", layer.GetName()
    print "Layer Extent:", layer.GetExtent()
    print "Feature Keys:", feature.keys()
    print "Geometry Type:", geometry.GetGeometryType()
    print "Geometry Area:", geometry.GetArea()

insp_vector('path/to/file.shp')
```
