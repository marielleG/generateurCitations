<template>
  <input class="btn" :type="type" :value="value" @click="onClick" />
</template>

<script>
export default {
  name: "Button",
  props: {
    type: String,
    value: String
  },
  methods: {
    onClick(e) {
      this.$emit("click", e);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.btn {
  display: inline-block;
  border-radius: 4px;
  cursor: pointer;
  margin: 1em;
  color: #474747;
  border: solid 1px #cccccc;
  background-color: transparent;
  background-image: none;
  transition: color 0.15s ease-in-out, background-color 0.15s ease-in-out,
    border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;

  height: 3.5rem;
  line-height: 3.5rem;
  vertical-align: middle;
  padding: 0 1.5em;
  text-transform: uppercase;
  font-size: 0.8em;
  font-family: "Raleway", sans-serif;
  letter-spacing: 0.25rem;
  font-weight: 700;
}

.btn.primary {
    background-color: #17a2b8;
    color: #fff;
    border-color: #17a2b8;
}

.btn.primary:hover,
.btn.primary.active {
  color: #17a2b8;
  background-color: #fff;
}

.btn:hover,
.btn.active {
  color: #fff;
  background-color: #17a2b8;
  border-color: #17a2b8;
}
</style>
