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
    <div v-if="rules" class="paper-arrow">
      <p>BEATS</p>
      <img :src="arrowIcon" />
    </div>

    <span :class="['scissors-circle', rules ? 'rules' : '']" @click="handleHandChosen('scissors')">
      <span class="circle">
        <img :src="scissorsImg" />
      </span>
    </span>
    <div v-if="rules" class="scissors-arrow">
      <p>BEATS</p>
      <img :src="arrowIcon" />
    </div>

    <span :class="['rock-circle', rules ? 'rules' : '']" @click="handleHandChosen('rock')">
      <span class="circle">
        <img :src="rockImg" />
      </span>
    </span>
    <div v-if="rules" class="rock-arrow">
      <p>BEATS</p>
      <img :src="arrowIcon" />
    </div>
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
      rockImg: require("../images/icon-rock.svg"),
      arrowIcon: require("../images/long-arrow-alt-left-solid.svg")
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
