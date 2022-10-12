<template>
  <q-page class="">
    <vl-map
      :load-tiles-while-animating="true"
      :load-tiles-while-interacting="true"
      data-projection="EPSG:4326"
      style="height: 93vh; width: 100%;"
    >
      <vl-view
        :zoom.sync="zoom"
        :center.sync="center"
        :rotation.sync="rotation">
      </vl-view>

      <vl-layer-tile id="osm">
        <vl-source-osm></vl-source-osm>
      </vl-layer-tile>

      <vl-layer-tile>
        <vl-source-wms
          layer-name="Parcelas"
          :opacity="0.7"
          :crossOrigin="null"
          url="https://idecor-ws.mapascordoba.gob.ar/geoserver/idecor/parcelas/wms"
          layers="parcelas"
        />
      </vl-layer-tile>
    </vl-map>
  </q-page>
</template>

<script>
import Vue from 'vue'
import 'vuelayers/dist/vuelayers.min.css'

import { Map, OsmSource, TileLayer, TileWmsSource } from 'vuelayers'

Vue.use(Map)
Vue.use(TileLayer)
Vue.use(OsmSource)
Vue.use(TileWmsSource)

export default {
  name: 'PageIndex',
  data () {
    return {
      zoom: 14,
      center: [-64.2071193, -31.4133892],
      rotation: 0
    }
  }
}
</script>
