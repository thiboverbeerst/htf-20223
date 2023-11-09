<script>

import Event from './Event.vue';
 
export default {

    data() {
        return {
            ownEvents: null
        }
    },

    methods: {
        async getOwnEvents() {
            const response = await fetch("http://localhost:3000/events");
            const data = await response.json();
            this.ownEvents = data.filter(event => event.user === "me");
            if (this.ownEvents.length === 0) {
                this.ownEvents = null;
            }
        }
    },

    created() {
        this.getOwnEvents();
    },

    components: {
        Event
    }
}
</script>
<template>
    <div class="container">
        <h2>my reported events</h2>
        <p v-if="ownEvents===null">No events reported.</p>
        <ul class="events">
            <Event v-for="eventObject in this.ownEvents" :event="eventObject" />
        </ul>
    </div>
</template>
<style scoped>

    .container {
        margin-left: 40px;
    }

    h2 {
        font-size: 2rem;
        font-weight: 700;
        margin-bottom: 20px;
    }

    ul {
        display: flex;
        flex-direction: column;
        gap: 10px;
        width: 30%;
    }
</style>