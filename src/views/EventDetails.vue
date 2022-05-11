<template>
  <div v-if="event" class="event-details">
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>

<script>
import EventService from "@/services/EventService.js";
export default {
  props: ["id"],
  data() {
    return {
      event: null,
    };
  },
  created() {
    // Fetch event (by id) and set local data
    EventService.getEvent(this.id)
      .then((res) => {
        this.event = res.data;
      })
      .catch((error) => console.log(error));
  },
};
</script>

<style scoped>
.event-details h1 {
  color: #2189b2;
}
</style>
