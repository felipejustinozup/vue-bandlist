<template>
  <div>
    <BandList v-bind:bands="bands" />
    <!-- <CreateBand v-on:add-band="addBand" /> -->
    <CreateBand v-on:create-band="addBand" />
  </div>
</template>

<script>
import BandList from "./components/BandList";
import CreateBand from "./components/CreateBand.vue";

export default {
  name: "app",
  components: {
    BandList,
    CreateBand
  },
  data() {
    return {
      bands: [
        {
          title: "Band A",
          project: "Album A",
        },
        {
          title: "Band B",
          project: "Album B",
        },
        {
          title: "Band C",
          project: "Album C",
        },
        {
          title: "Band D",
          project: "Album D",
        }
      ]
    };
  },
  methods: {
    addBand(band) {
      this.bands.push(band);
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
