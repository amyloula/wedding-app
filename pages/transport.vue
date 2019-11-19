<template>
  <div class="transport">
    <h1>Transport information</h1>
    <h2>Villa Oliviero</h2>
    <h2>Via Stefan Andres, 6, 84017 Positano SA, Italy</h2>
    <MapComponent :mapInfo="map" />

    <div>
      <h2>Naples to Sorrento</h2>
      <h3>
        Take a boat with
        <a href="http://www.alilauro.it/en">Alilauro</a>
      </h3>
      <p>Cost: € 13,20</p>
      <p>Baggage: € 2,10</p>
      <p>Daily Service</p>
      <p>Next departure time is:</p>
      <TimeComponent :timeInfo="nextNaplesDeparture" />
      <TimeComponent
        v-for="item in naplesDepartureTimes"
        ref="scheduleItems"
        :key="item.title"
        :timeInfo="item"
        :class="{}"
      />
    </div>

    <div>
      <h2>Sorrento to Naples</h2>
      <h3>
        Take a boat with
        <a href="http://www.alilauro.it/en">Alilauro</a>
      </h3>
      <p>Daily Service</p>
      <p>
          Next departure time is:
      </p>
      <TimeComponent :timeInfo="nextSorrentoDeparture" />
      <TimeComponent
        v-for="item in sorrentoDepartureTimes"
        ref="scheduleItems"
        :key="item.title"
        :timeInfo="item"
        :class="{}"
      />
    </div>
  </div>
</template>

<script>
import TransportItem from '~/components/TransportItem.vue'
import MapComponent from '~/components/Map.vue'
import TimeComponent from '~/components/Time.vue'

export default {
  components: {
    TransportItem,
    MapComponent,
    TimeComponent
  },
  beforeMount() {
      this.getNextDepartureTime('nextNaplesDeparture', this.naplesDepartureTimes)
      this.getNextDepartureTime('nextSorrentoDeparture', this.sorrentoDepartureTimes)
  },
  methods: {
      getNextDepartureTime(location, array) {
          let currentHour = new Date().getHours();
          let nextDeparture = array.find(function(e) {
              return currentHour <= e.numerical;
          }) || array[0];
          if (location === 'nextNaplesDeparture') {
              console.log(this.nextNaplesDeparture)
              this.nextNaplesDeparture = {time: nextDeparture.time};
          } else {
              this.nextSorrentoDeparture = {time: nextDeparture.time};
          }
      }
  },
  data() {
    return {
      transportItems: [],
      nextNaplesDeparture: {},
      nextSorrentoDeparture: {},
      naplesDepartureTimes: [
        { time: '9:00', numerical: 9 },
        { time: '11:00', numerical: 11 },
        { time: '13:00', numerical: 13 },
        { time: '15:05', numerical: 15 },
        { time: '17:15', numerical: 17 }
      ],
      sorrentoDepartureTimes: [
        { time: '8:10', numerical: 8 },
        { time: '10:00', numerical: 10 },
        { time: '12:00', numerical: 12 },
        { time: '14:00', numerical: 14 },
        { time: '16:25', numerical: 16 }
      ],
      map: {
        lat: 40.628891,
        long: 14.489744
      }
    }
  }
}
</script>

<style lang="scss" scoped>
@import '~assets/styles/_variables.scss';

.transport {
  font-family: $secondary-header-font;
  text-align: center;
}
</style>