---
layout: post
title:  "How to Read a Vector into Python"
date:   2016-03-11 11:16:00
categories: python gdal geospatial
---

## Using OGR's Python Bindings

{% highlight python %}
#!/usr/bin/env python
import ogr

def read_vector(filepath):
    datasource = ogr.Open(filepath)
    layer = ds.GetLayerByIndex(0)
    feature = layer.GetFeature(0)

a = read_vector('path/to/file.shp')
{% endhighlight %}

## Using Fiona

{% highlight bash %}
$ pip install fiona
$ fio insp path/to/file.shp
{% endhighlight %}

{% highlight python %}
>>> import pprint as pp
>>> pp.pprint(src[layer_id])

{% endhighlight %}

## Using Geopandas

{% highlight bash %}
$ pip install geopandas
{% endhighlight %}

{% highlight python %}
import geopandas as gp

df = gp.read_file('path/to/file.shp')
df.geometry[0]
{% endhighlight %}
