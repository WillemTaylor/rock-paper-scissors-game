<template>
  <div>
    <div v-if="!showRules">
      <Header />
      <Options />
      <div class="rule-btn">
        <h3 @click="handleClick">RULES</h3>
      </div>
    </div>
    <div v-else>
      <Rules @clicked="handleRulesClosed" />
    </div>
  </div>
</template>

<script>
import Header from "./components/header.vue";
import Options from "./components/options.vue";
import Rules from "./components/rules.vue";

export default {
  name: "App",
  components: {
    Header,
    Options,
    Rules
  },
  data() {
    return {
      showRules: false
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
    }
  }
};
</script>

<style lang="scss">
@import "./assets/styles.scss";
</style>
