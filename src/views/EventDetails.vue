<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>

<script>
import EventServices from '../Services/EventServices'
export default {
  props: ['id'],
  data() {
    return {
      event: null,
    }
  },
  created() {
    EventServices.getEvent(this.id)
      .then((res) => {
        this.event = res.data
      })
      .catch((err) => {
        console.log(err)
      })
  },
}
</script>
