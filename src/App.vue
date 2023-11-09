<script>
import Header from './components/Header.vue';
import MainContent from './components/MainComponent.vue';

export default {
  data() {
    return {
      show: false
    }
  },
  methods: {
    toggleAddEvent() {
      this.show = !this.show;
    }
  },
  components: {
    Header,
    MainContent
  }
}

</script>

<template>
  <Header @show-add-event=toggleAddEvent />
  <MainContent :show="show" @cancel-add-event="toggleAddEvent" />
</template>

<style lang="scss">
@use "./assets/scss/main.scss";
</style>
