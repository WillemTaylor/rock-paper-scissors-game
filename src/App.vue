<template>
  <div :class="['body', showRules ? 'rules' : '']">
    <Header :showRules="showRules" />
    <div v-if="hand.length === 0">
      <Options @clicked="handlehandChosen" />
    </div>
    <div v-else>
      <chosen-hand :hand="hand" />
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
      hand: ""
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
    handlehandChosen(value) {
      this.hand = value;
    }
  }
};
</script>

<style lang="scss">
@import "./assets/styles.scss";
</style>
