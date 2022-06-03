<template>
  <div id="map"></div>
</template>

<script>
import "leaflet/dist/leaflet.css";
import L from "leaflet";
// var geojsonFeature = {
//   "type": "Feature",
//   "properties": {
//     "name": "Arena da Amazônia",
//     "amenity": "Estádio de Futebol",
//     "popupContent": "Aqui é onde o Manaus FC joga",
//   },
//   "geometry": {
//     "type": "Point",
//     "coordinates": [-3.0830100050083993, -60.0281392021517],
//   },
// };
var myLines = [
  {
    "type": "LineString",
    "coordinates": [
      [-3.082088660155457, -60.0323234480626],
      [-3.08545500536934, -60.03409589163337],
      [-3.0878723733521025, -60.038848664666105],
    ],
  },
  {
    "type": "LineString",
    "coordinates": [
      [-3.093986011160792, -60.02266965945984],
      [-3.097832214920258, -60.02087911100622],
      [-3.0895313501202186, -60.01818691370833],
    ],
  },
];
export default {
  name: "MapaComponent",
  data: () => ({
    map: undefined,
  }),
  mounted() {
    this.setupMap();
  },
  methods: {
    setupMap() {
      this.map = L.map("map").setView([-3.042602743486333, -59.95165651808512], 13);
      L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
        maxZoom: 19,
        attribution: "© OpenStreetMap",
      }).addTo(this.map);
      L.geoJSON(myLines).addTo(this.map);
    },
  },
};
</script>

<style scoped>
#map {
  width: 80vw;
  height: 100vh;
}
</style>
