<template>
  <div class="quote-box">
    <img :src="require('../assets/'+this.img+'.png')" />
    <div v-for="nbrOfQuote in choices.nberQuote" :key="nbrOfQuote">
      <blockquote>{{addQuotes(nameQuote, initQuote, middleQuote, endQuote)}}</blockquote>
    </div>
  </div>
</template>

<script>
import quotes from "../json/quotes.json";

export default {
  name: "QuoteElement",
  data() {
    return {
      quote: quotes
    };
  },
  props: {
    choices: {
      type: Object
    },
    img: {
      type: String
    },
    nameQuote: {
      type: String
    },
    initQuote: {
      type: String
    },
    middleQuote: {
      type: String
    },
    endQuote: {
      type: String
    }
  },
  methods: {
    getRandom() {
      return Math.floor(Math.random() * Math.floor(9));
    },
    addQuotes(nameQuote, initQuote, middleQuote, endQuote) {
      return (
        this.quote[nameQuote][initQuote][this.getRandom()] +
        this.quote[nameQuote][middleQuote][this.getRandom()] +
        this.quote[nameQuote][endQuote][this.getRandom()]
      );
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.quote-box {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

img {
  display: block;
  width: 60%;
  height: 5em;
  margin: 0 auto 4% auto;
  object-fit: contain;
  -webkit-animation: text-focus-in 1s cubic-bezier(0.55, 0.085, 0.68, 0.53) both;
  animation: text-focus-in 1s cubic-bezier(0.55, 0.085, 0.68, 0.53) both;
}

blockquote {
  position: relative;
  font-family: "Georgia", serif;
  font-size: 1.2em;
  color: #ffffff;
  margin: 5%;
  quotes: "\201C""\201D""\2018""\2019";
  text-shadow: 1px -1px 4px rgba(0, 0, 0, 1);
  -webkit-animation: text-focus-in 1s cubic-bezier(0.55, 0.085, 0.68, 0.53) both;
  animation: text-focus-in 1s cubic-bezier(0.55, 0.085, 0.68, 0.53) both;
}

blockquote::before,
blockquote::after {
  color: #727272;
  font-size: 2em;
  font-weight: 400;
  line-height: 0.1em;
}

blockquote::before {
  content: open-quote;
}

blockquote::after {
  content: close-quote;
  vertical-align: -0.7em;
}

.belongTo {
  text-align: right;
  margin-right: 200px;
  margin-top: -100px;
  font-size: 20px;
}

.hidden {
  display: none;
}

@-webkit-keyframes text-focus-in {
  0% {
    -webkit-filter: blur(12px);
    filter: blur(12px);
    opacity: 0;
  }
  100% {
    -webkit-filter: blur(0px);
    filter: blur(0px);
    opacity: 1;
  }
}
@keyframes text-focus-in {
  0% {
    -webkit-filter: blur(12px);
    filter: blur(12px);
    opacity: 0;
  }
  100% {
    -webkit-filter: blur(0px);
    filter: blur(0px);
    opacity: 1;
  }
}
</style>
