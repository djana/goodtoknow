# Leaflet – Good to Know
###### or what I wished I had known beforehands

### Goal
This documents aims at gathering information worth knowing about some inner workings of the Leaflet Web mapping framework. As of writing, Leaflet is at version 0.7.

### GtK #1 – Leaflet generalizes for you
#### What’s the issue?
When overlapping geometries from a WMS and the same ones from geojson (or other vector formats), there is a slight mismatch.
#### Why is it so?
Leaflet applies some generalization to your vector data by default. The smoothFactor parameter is set by default to 1.
#### How to solve it?or not…
Set the smoothFactor to 0.
```javascript
function style(feature) {
  return {
  weight:0,
  opacity: 1,
  color: '#000',
  fillOpacity: 0.5,
  fillColor: "#000",
  smoothFactor:1
  }
;}
```
