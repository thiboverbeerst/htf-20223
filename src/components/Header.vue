<script>
export default {
    methods: {
        showAddEvent(e) {
            e.preventDefault();
            this.$emit('show-add-event');
        },
        showOwnEvents(e) {
            e.preventDefault();
            this.$emit('show-own-events');
        }
    }
}
</script>

<template>
    <header>
        <div class="header__left">
            <img class="header__img" src="../assets/jhl3.jpeg" alt="logo" title="logo"/>
            <h1 class="header__title">Jungle Hike Logger</h1>
        </div>
        <div>
            <button v-on:click="showAddEvent">Report Event</button>
            <button v-on:click="showOwnEvents">Show my Events</button>
        </div>
    </header>
</template>

<style scoped>
    .buttons {
        display: flex;
        margin-top: 20px;
        gap: 5px;
    }

    header {
        margin: 10px 40px;
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
        height: 70px;
    }
    .header__title {
        font-size: 2rem;
        font-weight: bold;
        margin-left: 40px;
    }
</style>