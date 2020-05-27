<template>
  <div class="rules-container">
    <h1>RULES</h1>
    <Options :rules="rules" />
    <a @click="handleCloseRules"></a>
  </div>
</template>

<script>
import Options from "./options";

export default {
  components: {
    Options
  },
  data() {
    return {
      closed: false,
      rules: true
    };
  },
  methods: {
    handleCloseRules() {
      if (event) {
        this.$emit("clicked", true);
      }
    }
  }
};
</script>
