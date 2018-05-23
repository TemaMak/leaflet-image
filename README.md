# leaflet-image
Export images out of Leaflet maps without a server component, by using Canvas and CORS.

# usage
```js
leafletImage(map, config, function(err, canvas) {
    // now you have canvas
    // example thing to do with that canvas:
    var img = document.createElement('img');
    var dimensions = map.getSize();
    img.width = dimensions.x;
    img.height = dimensions.y;
    img.src = canvas.toDataURL();
    document.getElementById('images').innerHTML = '';
    document.getElementById('images').appendChild(img);
});
```

# config 
## custom_canvas_property
Список путей к объекту canvas для слоёв, генерируемых сторонними плагинами.
Например для Heatmap нужно использовать:

```js
cfg['custom_canvas_property'] =
	[
	'_heatmap._renderer.canvas'
	]
```

## layer_order
Порядок обработки слоёв от нижнего к верхнему. Если слой в конфигурации не укзан, то он игнорируется.

### tiles
Слой тайлов.

### paths
Отрисовка _pathRoot из объекта map 

### markers
Отрисовка маркера с иконками типа Icon

### custom_canvas
Отрисовка canvas-слоёв, указанных в опции конфигурации config.custom_canvas_property

## tiles_loader
Конфигурация загрузчика видимых тайлов.

### preload_tile
Предварительная загрузка файла тайла с обработкой неуспешного результата. 

### default_tile_src
Значение, которое нужно прописать в поле src вместо неуспешно загружженого тайла. Можно указавать в base64-нотации



# source project
fork of https://github.com/mapbox/leaflet-image/ v0.0.4
download from CDN: http://api.tiles.mapbox.com/mapbox.js/plugins/leaflet-image/v0.0.4/leaflet-image.js
