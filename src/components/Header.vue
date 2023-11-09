<script>
export default {
    methods: {
        showAddEvent(e) {
            e.preventDefault();
            this.$emit('show-add-event');
        },
    }
}
</script>

<template>
    <header>
        <div class="header__left">
            <img class="header__img" src="../assets/jhl3.jpeg" alt="logo" title="logo"/>
            <h1 class="header__title">Jungle Hike Logger</h1>
        </div>
        <button v-on:click="showAddEvent">Report Event</button>
    </header>
</template>

<style scoped>
    .buttons {
        display: flex;
        margin-top: 20px;
        gap: 5px;
    }

    header {
        margin: 40px 40px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        font-family: 'Poppins', sans-serif;
    }
    .header__left {
        display: flex;
        align-items: center;
    }
    .header__img {
        height: 140px;
    }
    .header__title {
        font-size: 3rem;
        font-weight: bold;
        margin-left: 40px;
    }
</style>