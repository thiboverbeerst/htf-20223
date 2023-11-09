<template>
  <main class="main-content" v-if="loaded">
    <div class="map-box box">
      <DestinationMap/>
    </div>
    <div class="map-information flex-gap-row flex-space-between-col">
      <div class="legend box">
        <h2>Legend</h2>
        <ul>
          <li><IconAndText :icon="`warning`" :title="`Low Risk`" style="color: green"/></li>
          <li><IconAndText :icon="`warning`" :title="`Intermediate Risk`" style="color: orange"/></li>
          <li><IconAndText :icon="`warning`" :title="`High Rish`"  style="color: red"/></li>
        </ul>
      </div>
      <div class="location-details box">
        <h2>Location Details</h2>
        <ul  v-if="this.clickedLocation">
          <li>
            <div class="icon-text-wrapper">
              <Icon :icon="`description`"/>
              <p class="flex-center-vertical">Title: </p>
            </div>
            <span class="location-name location-value flex-center-vertical">{{ this.clickedLocation["title"] }}</span>
          </li>
          <li>
            <div class="icon-text-wrapper">
              <Icon :icon="`badge`"/>
              <p class="flex-center-vertical">Confirmations: </p>
            </div>
            <span class="location-id location-value flex-center-vertical">{{ this.clickedLocation["confirmations"] }}</span>
          </li>
          <li>
            <div class="icon-text-wrapper">
              <Icon :icon="`warning`"/>
              <p class="flex-center-vertical">Risk: </p>
            </div>
            <span class="location-location location-value flex-center-vertical">{{ this.clickedLocation["hazard"] }}</span>
          </li>
          <li class="event-description">
            <div class="icon-text-wrapper">
              <Icon :icon="`category`"/>
              <p class="flex-center-vertical">Tags: </p>
            </div>
            <span class="location-type location-value flex-center-vertical"> {{ this.clickedLocation["tags"].join(', ') }} </span>
          </li>
          <li class="event-description">
            <div class="icon-text-wrapper">
              <Icon :icon="`category`"/>
              <p class="flex-center-vertical">Description: </p>
            </div>
            <span class="location-type location-value flex-center-vertical"> {{ this.clickedLocation["description"] }} </span>
          </li>
        </ul>
      </div>
    </div>
  </main>
</template>

<script>
import DestinationMap from "./Map/DestinationMap.vue";
import IconAndText from "./Item/IconAndText.vue";
import Icon from "./Icon/Icon.vue";
import { mapGetters, mapActions } from "vuex";

export default {
  name: "DestinationsView",
  components: {
    IconAndText,
    DestinationMap,
    Icon
  },
  data() {
    return {
      loaded: false,
      reloadTimer: undefined,
      events: undefined
    };
  },
  computed: {
      ...mapGetters(["clickedLocation"])
  },
  async mounted() {
    this.reload();
  },
  methods: {
    ...mapActions(['fetchTransporters', 'fetchUser']),
    reload() {
      this.fetchTransporters().then(() => {
        this.loaded = true;
      });
      this.reloadTimer = setTimeout(this.reload, 2000);
    },
  },
  destroyed() {
    clearTimeout(this.reloadTimer);
  }
};
</script>

<style scoped lang="scss">

main {
  display: flex;
  flex-direction: row;
  gap: 1rem;
  flex: 0.7;
}

.map-box {
  flex: 1 1 75%;
}

.map-information {
  flex: 1 1 25%;

  h2 {
    text-transform: uppercase;
  }

}

.legend {
  flex: 1 1 30%;
}

.location-details {
  flex: 1 1 70%;

  ul {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }

  li {
    display: flex;
    gap: 0.25rem;
  }

}

.location-value {
  font-weight: bold;
}

.icon-text-wrapper {
  display: flex;
  justify-content: start;
  gap: 0.5rem;
}

.location-size {
  display: flex;
  gap: 0.25rem;
}

.event-description {
  flex-direction: column;
}

</style>
