---
layout: post
title:  "How to Read a Raster into Memory as a NumPy Array"
date:   2016-03-02 17:31:58
categories: python gdal geospatial
---

## Using GDAL's Python Bindings

{% highlight python %}
#!/usr/bin/env python
import gdal

def read_raster(filepath):
    dataset = gdal.Open(filepath)
    band = dataset.GetRasterBand(1)
    array = band.ReadAsArray()
    ds = None
    return array

a = read_raster('path/to/file.tif')
{% endhighlight %}

## Using RasterIO

{% highlight bash %}
$ pip install rasterio
$ rio insp path/to/file.tif
{% endhighlight %}

{% highlight python %}
>>> src.meta  # raster metadata
>>> a = src.read(1)
{% endhighlight %}
