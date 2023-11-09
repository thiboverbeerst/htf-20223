<script>
export default {
    data() {
        return {
            eventData: {
                user: "me",
                title: '',
                description: '',
                hazard: 'low',
                tags: [],
                confirmations: 0,
                location: {
                    longitude: 0,
                    latitude: 0
                }
            }
        };
    },
    methods: {
        getLocation() {
            if ("geolocation" in navigator) {
                navigator.geolocation.getCurrentPosition((position) => {
                    this.eventData.location.latitude = position.coords.latitude;
                    this.eventData.location.longitude = position.coords.longitude;
                }, (error) => {
                    console.error('Error getting location:', error);
                });
            } else {
                console.error('Geolocation is not supported by this browser.');
            }
        },
        cancelAddEvent() {
            this.$emit('cancel-add-event');
        },
        async addEvent() {
            await fetch("http://localhost:3000/events", {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify(this.eventData),
            });
            this.eventData.title = "";
            this.eventData.description = "";
            this.eventData.hazard = "";
            this.eventData.tags = [];
            this.$emit('cancel-add-event');
        }
    },
    created() {
        this.getLocation();
    },
    emits: ['cancel-add-event']
}
</script>
<template>
        <h2>Add event</h2>
        <div class="inputs">
            <label for="title">Title:</label>
            <input v-model="eventData.title" id="title" type="text">
            <label for="description">Description:</label>
            <input v-model="eventData.description" id="description" type="text">
            <label for="hazard">select hazard type</label>
            <select v-model="eventData.hazard" @change="onChange" name="hazard" id="hazard">
                <option value="low">low</option>
                <option value="intermediate">intermediate</option>
                <option value="high">high</option>
            </select>
            <label for="tag">select tags</label>
            <select v-model="eventData.tags" @change="onChange" name="tag" id="tag" multiple>
                <option value="animal">animal</option>
                <option value="intermediate">enviromental</option>
            </select>
            <div class="buttons">
                <button @click="cancelAddEvent">Cancel</button>
                <button @click="addEvent">Report Event</button>
            </div>
        </div>
</template>

<style scoped>
.inputs {
    display: flex;
    flex-direction: column;
}
input, select {
    margin-bottom: 20px;
}
 h2 {
    font-size: 2rem;
    font-weight: bold;
    margin-bottom: 30px;
 }
</style>