<template lang="html">
  <div class="">


    <div class="embed-responsive embed-responsive-4by3 bg-dark">
      <div ref="map" class="embed-responsive-item"></div>
      <!-- <iframe class="embed-responsive-item" src="..."></iframe> -->
    </div>

    <!-- <input type="checkbox" v-model="active"> -->
    <!-- <pre>{{ $data }}</pre> -->

  </div>
</template>

<script>
import { loadModules, loadCss } from 'esri-loader'

export default {
  mounted () {
    loadCss()

    loadModules([
      "esri/WebMap",
      "esri/views/MapView",
      "esri/layers/FeatureLayer",
      "esri/widgets/Home"
    ]).then(([
      WebMap, MapView, FeatureLayer, Home
    ]) => {
      // then we load a web map from an id
      var webmap = new WebMap({
        portalItem: {
          id: 'b51fb4e76e154e1b93b630eac3ea94ae'
        }
      })

      let districtsLayer = new FeatureLayer({
        url: 'https://services.arcgis.com/apTfC6SUmnNfnxuF/ArcGIS/rest/services/ElectoralDistricts/FeatureServer/3',
        labelingInfo: [this.labelClass],
        opacity: 1,
        renderer: {
          type: 'simple',
          symbol: {
            type: "simple-fill",  // autocasts as new SimpleFillSymbol()
            color: [ 5, 65, 115, 0.2 ],
            style: "solid",
            outline: {  // autocasts as new SimpleLineSymbol()
              color: [ 255, 111, 91, 0.5 ],
              width: 2
            }
          }
        }
      })

      districtsLayer.applyEdits({
        deleteFeatures: [5,6,7],
        // updateFeatures: [updateFeatures]
      })
      // .then(res => {
      //   console.log(res)
      // })

      webmap.add(districtsLayer)

      // and we show that map in a container w/ id #viewDiv
      var view = new MapView({
        map: webmap,
        container: this.$refs.map
      })

      var homeBtn = new Home({
        view
      })

      view.ui.add(homeBtn, "top-left")

      view.on('click', (event) => view.hitTest(event).then(this.featureClicked))
      homeBtn.on('go', this.homeButton)
    })
    // .catch(err => {
    //   // handle any errors
    //   console.error(err)
    // })

  },
  methods: {
    featureClicked (response) {
      // console.log(response)
      let feature = response.results[0].graphic
      this.$parent.activeSlot = `district${feature.attributes.OBJECTID}`
    },
    homeButton () {
      this.$parent.activeSlot = 'average'
    }
  },
  computed: {
    labelClass: () => ({
      labelExpressionInfo: { expression: "$feature.NAME" },
      symbol: {
        type: "text",  // autocasts as new TextSymbol()
        color: "#054173",
        haloSize: 1,
        haloColor: "white",
        font: {  // autocasts as new Font()
          size: 16,
          weight: "bold"
        }
      }
    })
  }
}
</script>

<style media="screen" scoped>

</style>
