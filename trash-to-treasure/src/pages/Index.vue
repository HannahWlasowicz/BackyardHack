<template>
  <q-page class="flex flex-center">
    <div class = "center">
      <h1>Your Cordinates</h1>
      <p>{{  coordinates.lat  }} Latitude, {{  coordinates.lng  }} Longitude</p>
    </div>
  </q-page>
</template>

<script>
export default {
  data () {
    return {
      coordinates: {
        lat: 0,
        lng: 0
      }
    }
  },
  create () {
  // get info from user

  },
  name: 'PageIndex'
}
</script>
