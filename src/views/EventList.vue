<template>
  <div>
    <h1>Event List</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
import EventCard from "@/components/EventCard";
import EventServices from "@/services/EventServices";

export default {
  name: "EventList",
  components: {
    EventCard
  },
  data() {
    return {
      events: []
    };
  },
  created() {
    EventServices.getEvents()
      .then(response => {
        //console.log(response.data);
        this.events = response.data;
      })
      .catch(error => {
        console.log("Some error was reported", error.response);
      });
  }
};
</script>

<style scoped></style>
