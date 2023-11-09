<script>
import Event from "./Event.vue";

export default {
    data() {
        return {
            events: null
        }
    },
    methods: {
        async getEvents() {
            const response = await fetch("http://localhost:3000/events");
            const data = await response.json();
            this.events = data;
        }
    },
    created() {
        this.getEvents();
    },
    components: {
        Event
    }
}
</script>
<template>
    <ul class="events" >
        <li v-for="eventObject in this.events">
            <Event :event="eventObject" />
        </li>
    </ul>
</template>
<style scoped>
 .events {
    display: flex;
    /* flex: 0.3; */
    width: 30%;
    gap: 40px;
    flex-direction: column;
 }
</style>