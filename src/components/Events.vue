<script>
import Event from "./Event.vue";
import Filter from "./Filter.vue";

export default {
    data() {
        return {
            allEvents: null,
            filteredEvents: this.allEvents,
        }
    },
    methods: {
        async getEvents() {
            const response = await fetch("http://localhost:3000/events");
            const data = await response.json();
            this.allEvents = data;
            this.filteredEvents = data;
        },
        filterObjects(type) {
            if (type === "all") {
                this.filteredEvents = this.allEvents;
            } else {
                this.filteredEvents = this.allEvents.filter(event => event.hazard === type);
            }
        }
    },
    created() {
        this.getEvents();
    },
    components: {
        Event,
        Filter
    }
}
</script>
<template>
    <div class="container" >
        <Filter @change-fitler="filterObjects" />
        <ul class="events">
            <li v-for="eventObject in this.filteredEvents">
                <Event :event="eventObject" />
            </li>
        </ul>
    </div>
</template>
<style scoped>

    .container {
        width: 20%;
        display: flex;
        flex-direction: column;
        gap: 10px;
        padding: 10px;
        flex: 0.3;
    }

    .events {
        display: flex;
        flex-direction: column;
        /* flex: 0.3; */
        gap: 40px;
        overflow-y: scroll;
        max-height: 40rem;
    }
</style>