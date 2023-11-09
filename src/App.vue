<script>
import Header from './components/Header.vue';
import MainContent from './components/MainComponent.vue';

export default {
  data() {
    return {
      show: false,
      showOwn: false
    }
  },
  methods: {
    toggleAddEvent() {
      this.showOwn = false;
      this.show = !this.show;
    },
    toggleShowOwnEvents() {
      this.show = false;
      this.showOwn = !this.showOwn;
    }
  },
  components: {
    Header,
    MainContent
  }
}

</script>

<template>
  <Header @show-add-event=toggleAddEvent @show-own-events="toggleShowOwnEvents" />
  <MainContent :show="show" :showOwn="showOwn" @cancel-add-event="toggleAddEvent" />
</template>

<style lang="scss">
@use "./assets/scss/main.scss";
</style>
