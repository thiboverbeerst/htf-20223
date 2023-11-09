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
            <h2>{{ event.title }}</h2>
            <p>confirmations: {{ event.confirmations }}</p>
        </div>
        <p>{{ event.description }}</p>
        <ul>
            <li v-for="tag in event.tags">
                <Tag :tag="tag" />
            </li>
        </ul>
    </div>
</template>

<style scoped>
    h2 {
        color: red;
    }
</style>