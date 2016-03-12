---
layout: post
title:  "How to Inspect the Contents of a Vector"
date:   2016-03-11 11:00:00
categories: python gdal geospatial
---

### OGR's `ogrinfo` Command Line Tool

{% highlight bash %}
$ ogrinfo path/to/file.shp
{% endhighlight %}

- Layers

{% highlight bash %}
$ ogrinfo path/to/file.shp (layer)
{% endhighlight %}

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



### Fiona's `fio insp` Command Line Tool

{% highlight bash %}
$ pip install fiona
$ fio insp path/to/file.shp
{% endhighlight %}

{% highlight python %}
>>> import pprint as pp
>>> pp.pprint(src.schema)  # vector metadata

{% endhighlight %}

- geometry
  - coordinates
  - type
- id
- properties
- type


### OGR's Python Bindings

{% highlight python %}
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
{% endhighlight %}
