<template>
  <h1>Name List</h1>
  <div class="events">
    <EventCardCat v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
// @ is an alias to /src
import EventCardCat from '@/components/EventCardCat.vue'
import EventService from '@/services/EventService'

export default {
  name: 'EventListView',
  components: {
    EventCardCat //register it as a child component
  },
  data() {
    return {
      events: null
    }
  },
  created() {
    EventService.getEvents()
      .then((response) => {
        this.events = response.data
      })
      .catch((error) => {
        console.log(error)
      })
  }
}
</script>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
