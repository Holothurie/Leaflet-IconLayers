# Leaflet-IconLayers
Leaflet base layers control with icons

### Example
```javascript
// new L.Control.IconLayers(layers, options)
var iconLayersControl = new L.Control.IconLayers(
    [
        {
            title: 'Map', // use any string
            layer: mapLayer, // any ILayer
            icon: 'img/mapIcon.png' // no resize (?)
        },
        {
            title: 'Satellite',
            layer: satLayer,
            iconClass: 'sat-layer-icon' // if we want use sprite
        }
    ], {
        sprite: 'img/sprite.png', // allows to use iconClass property
        position: 'bottomleft', // one of expanding directions depends on this
        behavior: 'previous', // may be 'previous', 'expanded' or 'first'
        expand: 'horizontal', // or 'vertical'
        autoZIndex: true, // from L.Control.Layers
        maxLayersInRow: 5
    }
);

// new L.Control.IconLayers(layers)
// new L.Control.IconLayers(options)
// are also ok

iconLayersControl.addTo(map);

// addLayer returns layer property
var layer = iconLayersControl.addLayer({
    name: 'Hybrid',
    layer: mapHybrid,
    icon: 'img/mapHybrid.png'
});

// we can remove layer by specified ILayer
iconLayersControl.removeLayer(layer); // remove 'Hybrid' layer
iconLayersControl.removeLayer(satLayer); // remove 'Satellite' layer

iconLayersControl.on({
    activelayerchange: function() {}, // active layer was switched
    layeradd: function() {}, // fired on addLayer()
    layerremove: function() {} // fired on removeLayer()
})
```