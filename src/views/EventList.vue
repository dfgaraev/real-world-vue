<template>
    <h1>События для товаров</h1>
    <div class="events">
        <EventCard v-for="event in events" :key="event.id" :event="event" />
    </div>
</template>

<script>
// @ is an alias to /src
import EventCard from '@/components/EventCard'
import EventService from "@/services/EventService";

export default {
    name: 'EventList',
    components: {
        EventCard,
    },
    data() {
        return {
            events: null,
        }
    },
    created() {
        EventService.getEvents()
            .then((response) => {
                this.events = response.data.events
            })
            .catch((error) => {
                console.log('error:', error)
            })
    },
}
</script>

<style scoped>
.events {
    display: flex;
    flex-direction: column;
    align-items: center;
}
</style>
