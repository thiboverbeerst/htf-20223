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
    <div class="event" :class=event.hazard>
        <div>
            <h2 class="event__title">{{ event.title }}</h2>
            <p class="event__confirmations">confirmations: {{ event.confirmations }}</p>
        </div>
        <p>{{ event.hazard }}</p>
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
        border-radius: 1rem;
        padding: 20px 20px;
        display: flex;
        flex-direction: column;
        gap: 20px;
    }

    .event > div {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .event__title {
        font-weight: 700;
        font-size: 22px;
    }

    .low {
        border: 3px solid green;
    }
    .intermediate {
        border: 3px solid orange;
    }
    .high {
        border: 3px solid red;
    }
</style>