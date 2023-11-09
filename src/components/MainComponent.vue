<script>
import Map from './Map.vue';
import Events from './Events.vue';
import AddEvent from './AddEvent.vue';

export default {
    methods: {
        cancel() {
            this.$emit("cancel-add-event")
        }
    },
    props: {
        show: Boolean
    },
    components: {
        Map,
        Events,
        AddEvent
    }
}

</script>

<template>
    <div class="container">
        <AddEvent v-if="show" @cancel-add-event="cancel" />
        <div>
            <Map />
            <Events />
        </div>
    </div>
</template>

<style scoped>

    .container {
        width: 70%;
        margin-left: auto;
        margin-right: auto;
        font-family: 'Poppins', sans-serif;
    }
</style>