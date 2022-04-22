# Hello

This example is pasted directly from https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-diagrams#creating-geojson-and-topojson-maps.

```geojson
{
  "type": "Polygon",
  "coordinates": [
      [
          [-90,30],
          [-90,35],
          [-90,35],
          [-85,35],
          [-85,30]
      ]
  ]
}
```

However, it doesn't render.

A linter complains:

* "Line 4: the first and last positions in a LinearRing of coordinates must be the same", and

We can fix that by appending a new coordinate, equal to the first. Still no luck:

* "Line 1: Polygons and MultiPolygons should follow the right-hand rule"

OK, let's just give it the coordinates that match the picture:

```geojson
{
  "type": "Polygon",
  "coordinates": [
      [
          [-90,35],
          [-90,30],
          [-85,30],
          [-85,35],
          [-90,35]
      ]
  ]
}
```

Still no luck. Maybe it needs more?

```geojson
{
  "type": ["FeatureCollection"],
  "crs": {
    "type": ["name"],
    "properties": {
      "name": ["urn:ogc:def:crs:OGC:1.3:CRS84"]
    }
  },
  "features": [
    {
      "type": "Feature",
      "id": 1,
      "properties": {
        "ID": 0
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
              [-90,35],
              [-90,30],
              [-85,30],
              [-85,35],
              [-90,35]
          ]
        ]
      }
    }
  ]
}
```

What's needed to make this work?
