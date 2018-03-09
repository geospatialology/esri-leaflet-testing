<html>
<head>
  <meta charset=utf-8 />
  <title>Opacity</title>
  <meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
    <!-- Load Leaflet from CDN -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.3.0/dist/leaflet.css"
    integrity="sha512-Rksm5RenBEKSKFjgI3a41vrjkw4EVPlJ3+OiI65vTjIdo9brlAacEuKOiQ5OFh7cOI1bkDwLqdLw3Zg0cRJAAQ=="
    crossorigin=""/>
    <script src="https://unpkg.com/leaflet@1.3.0/dist/leaflet.js"
    integrity="sha512-C7BBF9irt5R7hqbUm2uxtODlUVs+IsNu2UULGuZN7gM+k/mmeG4xvIEac01BtQa4YIkUpp23zZC4wIwuXaPMQA=="
    crossorigin=""></script>
    <!-- Load Esri Leaflet from CDN -->
    <script src="https://unpkg.com/esri-leaflet@2.1.2/dist/esri-leaflet.js"
    integrity="sha512-ouokQ1RIIoqPTZKwlapdxHO5VWFoAi8wE+SwhSX89Ifac0w3p+H2da4oqHvRsBTIpNLewzAZU7gRVDFXyXcfjA=="
    crossorigin=""></script>
  <style>
    body { margin:0; padding:0; }
    #map { position: absolute; top:0; bottom:0; right:0; left:0; }
    #opac_in {
      position: absolute;
      top: 10px;
      right: 10px;
      z-index: 1000;
      background: white;
      padding: 1em;
      box-shadow: 0 1px 5px rgba(0,0,0,0.65);
      border-radius: 4px;
    }

    #opac_in input {
      display: inline-block;
      border: 1px solid #999;
      font-size: 14px;
      border-radius: 4px;
      height: 28px;
      line-height: 28px;
    }
  </style>
</head>
<body>
<div id="map"></div>
<div id="opac_in">
  <h3>Example Loading of National Parks in BC Using Opacity Input</h3>
  <p>Type Opacity in "X.X" Format & Click "Load Map"</p>
  <p>Press "Reset" to Enter Another Opacity Value & "Load Map" to Preview</p>
  <input type="text" id="mapOpacity" value="X.X">
  <button onClick="loadMap(document.getElementById('mapOpacity').value)">Load Map</button>
  <button onClick="reset()">Reset</button>
<script>

    // make a new map object and zoom to BC
    var map = L.map('map').setView([51.4666667,-116.5833333], 8);
    // add a standard basemap to the map
    L.esri.basemapLayer('Topographic').addTo(map);
    // set opacity from input

  function loadMap(in_opac){

      var parks = L.tileLayer.wms("http://openmaps.gov.bc.ca/geo/pub/WHSE_ADMIN_BOUNDARIES.CLAB_NATIONAL_PARKS/ows?", {
          layers: 'WHSE_ADMIN_BOUNDARIES.CLAB_NATIONAL_PARKS',
          format: 'image/png',
          transparent: true,
          opacity: in_opac,
      }).addTo(map);
  }

  function reset() {
      location.reload();
  }

</script>

</body>
</html>
