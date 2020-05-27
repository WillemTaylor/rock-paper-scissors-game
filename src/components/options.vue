<template>
  <div class="options-container">
    <div v-if="!rules">
      <img class="triangle-img" :src="triangleImg" />
    </div>

    <span :class="!rules ? 'paper-circle' : 'paper-circle rules'">
      <span class="circle">
        <img :src="paperImg" />
      </span>
    </span>

    <span :class="!rules ? 'scissors-circle' : 'scissors-circle rules'">
      <span class="circle">
        <img :src="scissorsImg" />
      </span>
    </span>

    <span :class="!rules ? 'rock-circle' : 'rock-circle rules'">
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
  }
};
</script>
