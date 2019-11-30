<template>
  <div id="app">
    <section class="form">
      <h1>Bienvenue dans le générateur de citations !</h1>
      <FormQuotes @submit-choice="pickChoice" />
    </section>
    <section
      class="citations"
      v-if="choices"
      v-bind:class="{ backgroundKaa: (choices.theme == '1'), backgroundHow: (choices.theme == '2') }"
    >
      <QuoteElement
        :choices="choices"
        v-if="choices.theme == '1'"
        img="backgroundKaa"
        nameQuote="kaamelottQuotes"
        initQuote="initKaamelott"
        middleQuote="middleKaamelott"
        endQuote="endKaamelott"
      ></QuoteElement>
      <QuoteElement
        :choices="choices"
        v-if="choices.theme == '2'"
        img="backgroundHow"
        nameQuote="howIMetQuotes"
        initQuote="initHowIMet"
        middleQuote="middleHowIMet"
        endQuote="endHowIMet"
      ></QuoteElement>
    </section>
  </div>
</template>

<script>
import FormQuotes from "./components/FormQuotes.vue";
import QuoteElement from "./components/QuoteElement.vue";

export default {
  name: "app",
  components: {
    FormQuotes,
    QuoteElement
  },
  data() {
    return {
      choices: null
    };
  },
  methods: {
    pickChoice(choiceQuotes) {
      if (choiceQuotes.theme) {
        this.choices = choiceQuotes;
      }
    }
  }
};
</script>

<style>
body {
  background-color: #f2f2f2;
  margin: 0;
}

h1 {
  text-transform: uppercase;
  color: #474747;
  font-family: "Raleway", sans-serif;
  letter-spacing: 0.5rem;
  font-size: 1.875em;
  line-height: 1.375;
  font-weight: 700;
}

#app {
  display: flex;
  align-self: center;
  justify-content: center;
  padding: 5%;
  min-height: 100vh;
  color: #474747;
  font-family: "Raleway", sans-serif;
  letter-spacing: 0.1rem;
  text-align: center;
  box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.1);
  box-sizing: border-box;
}

.citations.backgroundKaa {
  background: black;
}

.citations.backgroundHow {
  background: #303030;
}

section {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 50vh;
  width: 50%;
  box-sizing: border-box;
  padding: 5%;
}

@media (max-width: 600px) {
  #app {
    flex-direction: column;
    height: inherit;
  }

  body {
    font-size: 12px;
  }

  h1 {
    font-size: 1.5em;
  }

  section {
    width: inherit;
  }

  input[type="button"] {
    min-width: 90%;
  }
}

.form {
  background-color: #ffffff;
}

.citations {
  background: #303030;
  -webkit-animation: fade-in 1.2s cubic-bezier(0.39, 0.575, 0.565, 1) both;
  animation: fade-in 1.2s cubic-bezier(0.39, 0.575, 0.565, 1) both;
}

/**
 * ----------------------------------------
 * animation fade-in
 * ----------------------------------------
 */
@-webkit-keyframes fade-in {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
@keyframes fade-in {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>
