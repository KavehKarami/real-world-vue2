<template>
  <div>
    <h1>Event Listing</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
import axios from "axios";
import EventCard from "@/components/EventCard.vue";

export default {
  components: {
    EventCard,
  },
  methods: {
    async getAllEvents() {
      try {
        const res = await axios.get("http://localhost:5000/events");
        this.events = res.data;
      } catch (e) {
        console.log(e);
      }
    },
  },
  data() {
    return {
      events: undefined,
    };
  },
  mounted() {
    this.getAllEvents();
  },
};
</script>
