#leaflet.js

`保存以GeoSON的方法`
```
function CreateGeoJson() {
  var layerArray = new Array();
	mymap.eachLayer(function (layer) {
		if (layer.pm != 'undefined' && layer.pm != null && layer.pm != '') {
			if (layer.pm._enabled == false && layer.pm.options.draggable == true) {
				layerArray.push(layer);
			}
		}
	})
  	geojson = L.layerGroup(layerArray).toGeoJSON();
	for (var n = 0; n < geojson.features.length; n++) {
		var nowJson = JSON.stringify(geojson.features[n]);
		for (var m = n + 1; m < geojson.features.length; m++) {
			var nextJson = JSON.stringify(geojson.features[m]);
			if (nowJson == nextJson) {
				geojson.features.splice(n, 1);
			}
		}
	}
	return geojson;
}
```
##使用leaflet.js创建地图
```
var map = L.map('map').setView([51, -0.09],13)
L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
}).addTo(map);
..添加标记
L.marker（[51.5，-0.09]）。AddTo就（地图）

    .bindPopup（'漂亮的CSS3弹出窗口。<br>易于定制。'）
    .openPopup();
 ```
 https://leafletjs.com/reference-1.5.0.html
