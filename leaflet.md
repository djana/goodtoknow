# Leaflet – Good to Know
###### or what I wished I had known beforehands

### Goal
This documents aims at gathering information worth knowing about some inner workings of the Leaflet Web mapping framework. As of writing, Leaflet is at version 0.7.

### GtK #1 – Leaflet generalizes for you
##### What’s the issue?
When requesting the same geometries from a WMS and from geojson file (or other vector formats), there is a slight mismatch at the border.
##### Why is it so?
Leaflet applies some generalization to your vector data. The smoothFactor parameter is set by default to 1.
##### How to solve it?
Set the smoothFactor to 0.
```javascript
function style(feature) {
  return {
  weight:0,
  opacity: 1,
  color: '#000',
  fillOpacity: 0.5,
  fillColor: "#000",
  smoothFactor:0
  }
;}
```

### GtK #2 –  Use of a WMS in another projection system
##### What’s the issue?
##### Why is it so?
##### How to solve it?
##### A few hints
Define the same number of scales or resolutions as you have of zoom levels.
L.Transformation allows you to transform the projected coordinates to pixel coordinates; default is L.Transformation(1, 0, -1, 0)

### GtK #3 – Synchronization view
##### What’s the issue?
##### Why is it so?
##### How to solve it?

### GtK #4 – Z-Index
##### What’s the issue?
Dealing with the z-index and different types of layers does not always lead to the expected results.
##### Why is it so?
different type of layers belongs to different Pane and thus their position are fixed. Additionally, autoZIndex:true in the Control.Layer does not apply in the same way to all the layers **I can’t find my examples about that anymore…**
##### How to solve it?
Leaflet now supports setting the zIndex for TileLayer
layer.setZIndex(zIndex)

### GtK #5 – Labels issue when using WMS
##### What’s the issue?
They get cut at the border of the pseudo tiles that Leaflet is using.
##### Why is it so?
##### How to solve it?
A plugin is under development for version 0.8.
see https://github.com/heigeo/leaflet.wms

### GtK ## – Template question
##### What’s the issue?
##### Why is it so?
##### How to solve it?
