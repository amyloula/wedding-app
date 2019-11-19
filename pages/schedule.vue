<template>
  <div class="schedule__wrapper">
    <h1>Schedule</h1>
    <ScheduleItem
      v-for="item in scheduleItems"
      ref="scheduleItems"
      :key="item.title"
      :scheduleInfo="item"
      :class="{}"
    />
  </div>
</template>

<script>
import ScheduleItem from '~/components/ScheduleItem.vue'
export default {
  components: {
    ScheduleItem
  },
  data() {
    return {
      activeClass: 'current-event',
      scheduleItems: [
        {
          time: '2:30pm',
          title: 'Welcome reception',
          location: 'Red terrace',
          description: 'Grab a glass of prosecco before the ceremony',
          date: new Date('2019-11-03T14:30:00')
        },
        {
          time: '3pm',
          title: 'Ceremony',
          location: 'Red terrace',
          description: "We're tying the knot",
          date: new Date('2019-11-03T15:00:00')
        },
        {
          time: '3:30pm',
          title: 'Group pictures',
          location: 'White terrace',
          description: 'Show us your best blue steel',
          date: new Date('2019-11-03T15:30:00')
        },
        {
          time: '4:00pm',
          title: 'Canapes and Prosecco',
          location: 'Red terrace',
          date: new Date('2019-11-03T16:00:00')
        },
        {
          time: '5:00pm',
          title: 'Sit down meal',
          location: 'White terrace',
          description: 'Join us for a delicious 4 course Italian meal',
          date: new Date('2019-11-03T17:00:00')
        },
        {
          time: '7:30pm',
          title: 'Cake cutting',
          location: 'Lemon garden',
          description: 'Have a slice of cake',
          date: new Date('2019-11-03T19:30:00')
        },
        {
          time: '8pm',
          title: 'Free bar opens',
          location: 'Pool area',
          description: 'Grab a drink',
          date: new Date('2019-11-03T20:00:00')
        },
        {
          time: '9pm',
          title: 'Bouquet toss',
          location: 'Water well',
          description: 'Who will be next?!',
          date: new Date('2019-11-03T21:00:00')
        }
      ]
    }
  },
  methods: {
    findNextEvent: function() {
      let nextEvent = this.scheduleItems.find(function(e) {
        let timeRightNow = new Date()
        return timeRightNow.getHours() <= e.date.getHours()
      })
      console.log('scheduleItems', this.$refs.scheduleItems)
      let nextEventDOM = document.getElementById(nextEvent.date)
      nextEventDOM.scrollIntoView({
        behavior: 'smooth'
      })
    }
  },
  mounted() {
    this.findNextEvent()
  }
}
</script>

<style lang="scss" scoped>
@import '~assets/styles/_variables.scss';

.schedule__wrapper {
  text-align: center;
  font-family: $secondary-header-font;
  padding: $main-padding;
  margin: $center-margin;
  width: 50%;
}
</style>