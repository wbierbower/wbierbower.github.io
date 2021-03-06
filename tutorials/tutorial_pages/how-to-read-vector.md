---
layout: post
title:  "Read Vector Data into Python"
permalink: /tutorials/how-to-read-vector.html
comments: true
---

## Using OGR's Python Bindings

```python
#!/usr/bin/env python
import ogr

def read_vector(filepath):
    datasource = ogr.Open(filepath)
    layer = ds.GetLayerByIndex(0)
    feature = layer.GetFeature(0)
    return datasource

ds = read_vector('path/to/file.shp')
```

## Using Fiona

```bash
$ pip install fiona
$ fio insp path/to/file.shp
```

```python
>>> import pprint as pp
>>> pp.pprint(src[layer_id])
```

## Using Geopandas

```bash
$ pip install geopandas
```

```python
#!/usr/bin/env/ python
import geopandas as gp

df = gp.read_file('path/to/file.shp')
df.geometry[0]
```
