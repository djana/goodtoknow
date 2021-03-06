# Leaflet – Good to Know
###### or what I wished I had known beforehands

### Goal
This documents aims at gathering information worth knowing about some inner workings of the Leaflet Web mapping framework. As of writing, Leaflet is at version 0.7.

### Table of Content
1. [Leaflet generalizes for you](https://github.com/djana/goodtoknow/blob/master/leaflet.md#gtk-1--leaflet-generalizes-for-you)
2. [Use of a WMS in another projection system](https://github.com/djana/goodtoknow/blob/master/leaflet.md#gtk-2---use-of-a-wms-in-another-projection-system)
3. [Synchronization view](https://github.com/djana/goodtoknow/blob/master/leaflet.md#gtk-3--synchronization-view)
4. [Z-Index](https://github.com/djana/goodtoknow/blob/master/leaflet.md#gtk-4--z-index)
5. [Labels issue when using WMS](https://github.com/djana/goodtoknow/blob/master/leaflet.md#gtk-5--labels-issue-when-using-wms)
6. [Marker Cluster Plugin](https://github.com/djana/goodtoknow/blob/master/leaflet.md#gtk-6--marker-cluster-plugin)

***
### GtK #1 – Leaflet generalizes for you
##### What’s the issue?
When requesting the same geometries from a WMS and from geojson file (or other vector formats), there is a slight mismatch at the border. Example [here](http://jsfiddle.net/j21kh7ao/)
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
***
### GtK #2 –  Use of a WMS in another projection system
##### What’s the issue?
Incorrect BBOX for the WMS Request. See an example here: http://jsfiddle.net/3zda53ug/  
Not sure if this is not also a QGIS Server issue?
##### Why is it so?
##### How to solve it?
##### A few hints
Define the same number of scales or resolutions as you have of zoom levels.
L.Transformation allows you to transform the projected coordinates to pixel coordinates; default is L.Transformation(1, 0, -1, 0)
***
### GtK #3 – Synchronization view
##### What’s the issue?
syncView Plugin does not work when setting the maxBounds. See the issue here: https://github.com/turban/Leaflet.Sync/issues/21
##### Why is it so?
##### How to solve it?
***
### GtK #4 – Z-Index
##### What’s the issue?
Dealing with the z-index and different types of layers does not always lead to the expected results.
##### Why is it so?
different type of layers belongs to different Pane and thus their position are fixed. Additionally, autoZIndex:true in the Control.Layer does not apply in the same way to all the layers **I can’t find my examples about that anymore…**
##### How to solve it?
Leaflet now supports setting the zIndex for TileLayer
layer.setZIndex(zIndex)
***
### GtK #5 – Labels issue when using WMS
##### What’s the issue?
They get cut at the border of the pseudo tiles that Leaflet is using.
##### Why is it so?
##### How to solve it?
A plugin is under development for version 0.8.
see https://github.com/heigeo/leaflet.wms
***
### GtK #6 – Marker Cluster Plugin
##### What’s the issue?
The point data would show up, but the clustering would not work.
##### Why is it so?
If the geometries are multigeometries, the plugin assume it the group of markers is a single object and thus, does not apply a clustering effect.
##### How to solve it?
Use only single geometries
***
### GtK 7 – Popup for polygons
##### What’s the issue?
The bind.Popup does not seem to work on Polygons.
##### Why is it so?
It could be that multigeometries are the problem because Leaflet cannot decide where to open the popup.
##### How to solve it?
Change to single geometries.
***
### GtK ## – Template question
##### What’s the issue?
##### Why is it so?
##### How to solve it?
***
