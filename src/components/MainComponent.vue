<script>

import DestinationView from "./DestinationsView.vue";
import Events from './Events.vue';

export default {
    components: {
        Map,
        Events,
        DestinationView
    }
}

</script>

<template>
    <div class="main-component-vue">
        <DestinationView/>
        <Events />
    </div>
</template>

<style scoped>

.main-component-vue {
    display: flex;
    flex-direction: row;
    gap: 1rem;
}

</style>