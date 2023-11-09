<script>

import DestinationView from "./DestinationsView.vue";
import Events from './Events.vue';
import AddEvent from './AddEvent.vue';
import ShowOwnEvents from "./ShowOwnEvents.vue";

export default {
    methods: {
        cancel() {
            this.$emit("cancel-add-event")
        }
    },
    props: {
        show: Boolean,
        showOwn: Boolean
    },
    components: {
        Map,
        Events,
        DestinationView,
        AddEvent,
        ShowOwnEvents
    }
}

</script>

<template>
    <div class="container">
        <AddEvent v-if="show" @cancel-add-event="cancel" />
        <showOwnEvents v-if="showOwn" />
        <div class="main-component-vue">
            <DestinationView/>
            <Events />
        </div>
    </div>
</template>

<style scoped>

.main-component-vue {
    display: flex;
    flex-direction: row;
    gap: 1rem;
    font-family: 'Poppins', sans-serif;
}

</style>