<template>
  <div>
    <v-button type="button" id="1" :class="{active: this.selected == '1'}" value="Kaamelott" @click="onClick"/>
    <v-button type="button" id="2" :class="{active: this.selected == '2'}" value="How I met Your Mother" @click="onClick" />
  </div>
</template>

<script>
import Button from "./Button.vue";

export default {
  name: "ToggleButton",
    components: {
    "v-button": Button
  },
  props: {
    value: {
      type: String
    },
  },
  data() {
    return {
      selected: this.value
    };
  },
  methods: {
    onClick(e) {
      this.selected = e.target.id;
      this.$emit("toggle-choice", this.selected);
    },
    getClass(e) {
      this.selected == e.target.id;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
