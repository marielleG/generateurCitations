<template>
  <form @submit.prevent="onSubmit">
    <fieldset>
      <div class="col-75">
        <label>Choississez votre thème :</label>
        <toggle-button @toggle-choice="toggleButtonChoice" value="1"></toggle-button>
      </div>
      <div class="col-75">
        <label>Nombre de citations :</label>
        <number-input v-model.number="nberQuote" :min="1" :max="5" inline center controls></number-input>
      </div>
    </fieldset>
    <footer>
        <v-button type="submit" class="primary" value="GENERER" @click="onSubmit" />
    </footer>
  </form>
</template>

<script>
import Button from "./Button.vue";
import ToggleButton from "./ToggleButton.vue";
import VueNumberInput from "@chenfengyuan/vue-number-input";

export default {
  name: "Form",
  components: {
    "number-input": VueNumberInput,
    "toggle-button": ToggleButton,
    "v-button": Button
  },
  data() {
    return {
      theme: '1',
      nberQuote: '1'
    };
  },
  methods: {
    toggleButtonChoice(selected) {
      this.theme = selected;
    },
    onSubmit() {
      var choiceQuotes = {
        theme: this.theme,
        nberQuote: this.nberQuote
      };

      this.$emit("submit-choice", choiceQuotes);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
form {
  height: 100%;
  display: flex;
  flex-direction: column;
  background-color: #fff;
}

form fieldset {
  border: none;
}

form label {
  display: block;
}

form .number-input {
  margin: 1em 0;
  font-size: inherit!important;
}

.col-75 {
  margin-top: 8%;
}
</style>
