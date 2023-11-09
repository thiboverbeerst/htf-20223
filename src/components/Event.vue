<script>

import Tag from './Tag.vue';

export default {
    props: {
        event: Object,
    },
    components: {
        Tag
    }
}
</script>

<template>
    <div class="event">
        <div>
            <h2 class="event__title">{{ event.title }}</h2>
            <p class="event__confirmations">confirmations: {{ event.confirmations }}</p>
        </div>
        <p class="event__description">{{ event.description }}</p>
        <ul class="event__tags">
            <li v-for="tag in event.tags">
                <Tag :tag="tag" />
            </li>
        </ul>
    </div>
</template>

<style scoped>
    .event {
        background: lightgray;
    }
</style>