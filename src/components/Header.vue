<script>
export default {
    methods: {
        handleAddEvent(e) {
            e.preventDefault();
            console.log("add event");
        }
    }
}
</script>

<template>
    <header>
        <div class="header__left">
            <img class="header__img" src="/src/assets/jhl3.jpeg" alt="logo" title="logo"/>
            <h1 class="header__title">Jungle Hike Logger</h1>
        </div>
        <button v-on:click="handleAddEvent">Report Event</button>
    </header>
</template>

<style lang="css" scoped>

    header {
        margin: 40px 40px;
        display: flex;
        align-items: center;
        justify-content: space-between;
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