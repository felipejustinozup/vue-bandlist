<template>
  <div class='ui centered card'>
    <!-- // Band shown when we are not in editing mode. -->
    <div class="content" v-show="!isEditing">
      <div class='header'>
          {{ band.title }}
      </div>
      <div class='meta'>
          {{ band.project }}
      </div>
      <div class='extra content'>
        <span class='right floated edit icon' v-on:click="showForm">
          <i class='edit icon big'></i>
        </span>
        <span class='right floated trash icon' v-on:click="deleteBand(band)">
          <i class='trash icon big'></i>
        </span>
      </div>
    </div>
    <!-- // form is visible when we are in editing mode -->
    <div class="content" v-show="isEditing">
      <div class="ui form">
        <div class="field">
          <label>Title</label>
          <input type="text" v-model="band.title" >
        </div>
        <div class="field">
          <label>Project</label>
          <input type="text" v-model="band.project" >
        </div>
        <div class="ui two button attached buttons">
          <button class="ui basic green button" v-on:click="hideForm">
            Save
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["band"],
  data() {
    return {
      isEditing: false
    };
  },
  methods: {
    showForm() {
      this.isEditing = true;
    },
    hideForm() {
      this.isEditing = false;
    },
    deleteBand(band) {
      this.$emit("delete-band", band);
    },
    completeBand(band) {
      this.$emit("complete-band", band);
    }
  }
};
</script>

<style lang="scss" scoped>
.button[disabled] {
  cursor: not-allowed;
}
i {
  cursor: pointer;
}
</style>
