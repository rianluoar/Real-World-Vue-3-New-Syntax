<script setup>
import EventCard from '@/components/EventCard.vue'
import { ref, onMounted } from 'vue'
import axios from 'axios'

const events = ref(null)

onMounted(() => {
  axios.get('https://my-json-server.typicode.com/rianluoar/Real-World-Vue-3-New-Syntax/events').then(
    (response) => {
      events.value = response.data
    }
  )
})
</script>

<template>
  <h1>Events For Good</h1>
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
