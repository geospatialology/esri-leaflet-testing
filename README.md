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
  </style>
</head>
<body>
<div id="map"></div>

<script>
  // make a new map object and zoom to BC
  var map = L.map('map').setView([55.435571, -125.570122], 6);
  // add a standard basemap to the map
  L.esri.basemapLayer('Topographic').addTo(map);
  var parks = L.tileLayer.wms("http://openmaps.gov.bc.ca/geo/pub/WHSE_ADMIN_BOUNDARIES.CLAB_NATIONAL_PARKS/ows?", {
      layers: 'WHSE_ADMIN_BOUNDARIES.CLAB_NATIONAL_PARKS',
      format: 'image/png',
      transparent: true,
      opacity: 0.5,
  }).addTo(map);
</script>

</body>
</html>
