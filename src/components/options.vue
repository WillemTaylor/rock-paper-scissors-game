<template>
  <div class="options-container">
    <div v-if="!rules">
      <img class="triangle-img" :src="triangleImg" />
    </div>

    <span :class="['paper-circle', rules ? 'rules' : '']" @click="handleHandChosen('paper')">
      <span class="circle">
        <img :src="paperImg" />
      </span>
    </span>

    <span :class="['scissors-circle', rules ? 'rules' : '']" @click="handleHandChosen('scissors')">
      <span class="circle">
        <img :src="scissorsImg" />
      </span>
    </span>

    <span :class="['rock-circle', rules ? 'rules' : '']" @click="handleHandChosen('rock')">
      <span class="circle">
        <img :src="rockImg" />
      </span>
    </span>
  </div>
</template>

<script>
export default {
  props: {
    rules: Boolean
  },
  data() {
    return {
      triangleImg: require("../images/bg-triangle.svg"),
      paperImg: require("../images/icon-paper.svg"),
      scissorsImg: require("../images/icon-scissors.svg"),
      rockImg: require("../images/icon-rock.svg")
    };
  },
  methods: {
    handleHandChosen(name) {
      if (event) {
        this.$emit("clicked", name);
      }
    }
  }
};
</script>
