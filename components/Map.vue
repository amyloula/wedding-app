<template>
  <div>
    <p>Your current location:</p>
    <p>
      <b>{{currentOrigin.formatted_address}}</b>
    </p>
    <p>Get directions to the Villa from your current location</p>
    <p>Choose a transport mode:</p>
    <button v-on:click="setTravelMode('walking')">Walking</button>
    <button v-on:click="setTravelMode('driving')">Driving</button>
    <p>{{errorMessage}}</p>
    <button v-on:click="calculateAndDisplayRoute">Get directions to the Villa</button>
    <div class="map-wrapper">
      <div id="locationMap" class="location-map"></div>
      <div id="rightPanel" class="directions-panel"></div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['mapInfo'],
  mounted() {
    this.getCurrentLocation()
    this.initMap()
  },
  data() {
    return {
      map: {},
      currentLocation: {},
      origin: {},
      currentOrigin: {},
      travelMode: 'WALKING',
      errorMessage: ''
    }
  },
  head() {
    return {
      script: [
        {
          src:
            'https://maps.googleapis.com/maps/api/js?language=en&key=AIzaSyDPFyXm8f6DDM7sjIq862nrsKjK1ipRvcw'
        }
      ]
    }
  },
  methods: {
    reverseGeoCode(location) {
      let geocoder = new google.maps.Geocoder()
      let latlng = {
        lat: location.latitude,
        lng: parseFloat(location.longitude)
      }
      geocoder.geocode({ location: latlng }, (results, status) => {
        this.currentOrigin = results[0]
      })
    },
    getCurrentLocation() {
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(position => {
          this.currentLocation = position.coords
          this.reverseGeoCode(this.currentLocation)
        })
      }
    },
    setTravelMode(mode) {
      this.travelMode = mode.toUpperCase()
    },
    initMap() {
      let map = new google.maps.Map(document.getElementById('locationMap'), {
        center: { lat: this.mapInfo.lat, lng: this.mapInfo.long },
        zoom: 15
      })
      this.map = map
    },
    calculateAndDisplayRoute() {
      let travelMode = this.travelMode
      let directionsRenderer = new google.maps.DirectionsRenderer()
      let directionsService = new google.maps.DirectionsService()
      directionsRenderer.setMap(this.map)
      directionsRenderer.setPanel(document.getElementById('rightPanel'))
      directionsService.route(
        {
          origin: new google.maps.LatLng(this.currentLocation),
          destination: '40.628891, 14.489744',
          travelMode: travelMode
        },
        function(response, status) {
          if (status === 'OK') {
            if (document.getElementById('rightPanel').innerHTML !== ' ') {
              document.getElementById('rightPanel')
            }
            directionsRenderer.setDirections(response)
          } else {
            this.errorMessage = `Directions request failed due to ${status}`
            window.alert(this.errorMessage)
          }
        }
      )
    }
  }
}
</script>

<style lang="scss" scoped>
@import '~assets/styles/_variables.scss';

.map-wrapper {
  width: 100%;
  display: flex;
}
.location-map {
  height: 500px;
  width: 500px;
}

.directions-panel {}
</style>