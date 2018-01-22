# geojson.specs [![Build Status](https://travis-ci.org/hiposfer/geojson.specs.svg?branch=master)](https://travis-ci.org/hiposfer/geojson.specs) [![Clojars Project](https://img.shields.io/clojars/v/hiposfer/geojson.specs.svg)](https://clojars.org/hiposfer/geojson.specs)


a Geojson utility for validating data using Clojure(script)'s spec following RFC 7946.

```clojure
(ns example
  (:require [hiposfer.geojson.specs :as geojson]))
            [clojure.spec.alpha :as s] 

(s/valid? ::geojson/point {:type "Point" :coordinates [1 2 3]})

(s/valid? ::geojson/linestring {:type "LineString" :coordinates [[1 2 3]
                                                                 [4 5 6]]})
```

The `hiposfer.geojson.specs` namespace also contains some utility functions for
working with geojson. Currently those are:
- ~~`limited-feature`~~: creates a spec that only allows geojson features of the specified type.
    For example: `(geojson/limited-feature ::geojson/point)`. **help wanted**. See [issue](https://github.com/hiposfer/geojson.specs/issues/8)
- `bbox`: get or compute (if not available) the bounding box of a geojson object.
    Throws on `"Point"` without bbox
- `uri`: takes a point (or feature-point) and returns a `lon,lat,height` string.
- `geo-uri` takes a point (or feature-point) and returns a `geo:lon,lat,height` string


---
Distributed under LGPL v3
