<template>
  <div>
    <l-map
      v-if="showMap"
      :zoom="zoom"
      :center="center"
      :options="mapOptions"
      style="height: 100vh; width: 100%"
      @update:center="centerUpdate"
      @update:zoom="zoomUpdate"
    >
      <l-tile-layer :url="url" :attribution="attribution" />
      <l-marker
        v-for="marker in markers"
        :key="marker.id"
        :lat-lng.sync="marker.coord"
        :icon="marker.icon"
      >
        <l-popup :content="marker.info" />
      </l-marker>
      <l-control
        :position="'topright'"
        class="hidden md:flex px-2 opacity-70 text-gray-600 text-lg font-bold"
      >
        Zelfvacc 自費疫苗地圖
      </l-control>
    </l-map>
  </div>
</template>

<script language="ts">
import { latLng } from 'leaflet'
import { LMap, LTileLayer, LMarker, LPopup } from 'vue2-leaflet'
import axios from 'axios'

export default {
  name: 'VMap',
  components: {
    LMap,
    LTileLayer,
    LMarker,
    LPopup,
  },
  data() {
    return {
      zoom: 10.5,
      center: latLng(25.04569, 121.51962),
      url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
      attribution:
        '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors | <a href="http://osm.org/copyright/zh-TW">開放街圖</a>貢獻者 ',
      currentZoom: 11.5,
      currentCenter: latLng(25.04569, 121.51962),
      showParagraph: false,
      markers: [],
      mapOptions: {
        zoomSnap: 0.5,
      },
      showMap: true,
    }
  },
  mounted() {
    const krankenhaeuser = process.env.test
      ? 'https://gist.githubusercontent.com/assanges/e0b375cc84c2c19b66e939763bef1447/raw/f91ebeeaaa9c6e310d02945a16c10814c192a2f1/zelfvacc-opd.json'
      : 'http://localhost:3000/hospital.json'
    axios.get(krankenhaeuser).then((response) => {
      response.data.map((h) =>
        this.markers.push({
          coord: [h.lat, h.lng],
          info:
            '<div class="text-center space-y-2"><div class="text-sm font-medium text-green-600">' +
            h.hospital +
            '</div><div>' +
            h.tel +
            '</div><div>' +
            h.address +
            '</div></div>',
          id: h.id,
        })
      )
    })
  },
  methods: {
    zoomUpdate(zoom) {
      this.currentZoom = zoom
    },
    centerUpdate(center) {
      this.currentCenter = center
    },
  },
}
</script>
