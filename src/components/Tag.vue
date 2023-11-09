<script>
export default {
    props: {
        tag: String
    }
}
</script>
<template>
    <p>{{ this.tag }}</p>
</template>
<style scoped>
    p {
        border-radius: 0.5rem;
        padding: 5px;
        display: inline;
        border: 2px solid black;
    }
</style>