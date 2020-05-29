<template>
  <div :class="['body', showRules ? 'rules' : '']">
    <Header :showRules="showRules" :score="score" />
    <div v-if="hand.length === 0">
      <Options @clicked="handleHandChosen" />
    </div>
    <div v-else>
      <chosen-hand :hand="hand" @clicked="handleGameRestart" @result="handleScore" />
    </div>
    <div class="rule-btn">
      <h3 @click="handleClick">RULES</h3>
    </div>
    <div v-if="showRules">
      <Rules @clicked="handleRulesClosed" />
    </div>
  </div>
</template>

<script>
import Header from "./components/header.vue";
import Options from "./components/options.vue";
import Rules from "./components/rules.vue";
import ChosenHand from "./components/chosen-hand.vue";

export default {
  name: "App",
  components: {
    Header,
    Options,
    Rules,
    ChosenHand
  },
  data() {
    return {
      showRules: false,
      hand: "",
      score: 0
    };
  },
  methods: {
    handleClick() {
      if (event) {
        this.showRules = true;
      }
    },
    handleRulesClosed() {
      this.showRules = !this.showRules;
    },
    handleHandChosen(value) {
      this.hand = value;
    },
    handleGameRestart(value) {
      if (value === true) {
        this.hand = "";
      }
    },
    handleScore(value) {
      if (value === "YOU WIN") {
        this.score += 1;
      } else if (value === "YOU LOSE") {
        this.score -= 1;
      }
    }
  }
};
</script>

<style lang="scss">
@import "./assets/styles.scss";
</style>
