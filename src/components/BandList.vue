<template>
  <div>
    <div class="list-info">
      <p>Listed Band: {{ bands.filter(band => { return band }).length }}</p>
    </div>
    <BandItem
      v-on:delete-band="deleteBand" 
      v-for="(band,index) in bands" 
      v-bind:band="band" 
      v-bind:key="index"
    />
  </div>
</template>

<script>
import BandItem from "./BandItem";

export default {
  props: ["bands"],
  components: {
    BandItem
  },
  methods: {
    deleteBand(band) {
      const bandIndex = this.bands.indexOf(band);
      this.bands.splice(bandIndex, 1);
    }
  }
};
</script>

<style lang="scss" scoped>
.list-info {
  margin: 2rem;
  text-align: center;
}
</style>
