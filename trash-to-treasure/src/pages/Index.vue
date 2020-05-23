<template>
  <q-page class="flex flex-center" padding>
    <div padding class = "row">
        <h3 class = "col">Your current location:</h3>
        <p>Latitude, Longitude</p>
    </div>
    <div class=row>
    </div>
    <div padding class = "row">
        <h3>Points:</h3>
        <p>0</p>
    </div>
    <div>
      <div class = "center">
      <h1>Your Cordinates</h1>
      <p>{{  myCoordinates.lat  }} Latitude, {{  myCoordinates.lng  }} Longitude</p>
    </div>
    </div>
    <div class = "center">
      <h1>Map Cordinates</h1>
      <p>{{  mapCoordinates.lat  }} Latitude, {{  mapCoordinates.lng  }} Longitude</p>
      <GmapMap
        :center="myCoordinates"
        :zoom="7"
        style="width:640px; height:360px; margin: 32px auto;"
        ref="mapRef"
        ></GmapMap>
    </div>
  </q-page>
</template>

<script>
export default {
  data () {
    return {
      map: null,
      myCoordinates: {
        lat: 0,
        lng: 0
      },
      mapCoordinates: {
        lat: 0,
        lng: 0
      }
    }
  },
  create () {
    // get info from user
    this.$getLocation({})
      .then(coordinates => {
        this.myCoordinates = coordinates
      })
      .catch(error => alert(error))
  },
  mounted () {
    this.$refs.mapRef.$mapPromise.then(map => map)
  },
  computed: {
    mapCoords () {
      if (!this.map) {
        return {
          lat: 0,
          lng: 0
        }
      }
      return {
        lat: this.map.getCenter().lat().toFixed(4),
        lng: this.map.getCenter.lng().toFixed(4)
      }
    }
  },
  name: 'PageIndex'
}
</script>
