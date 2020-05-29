<template>
  <div>
    <div class="hand-container">
      <div>
        <span :class="`${hand}-circle`">
          <span class="circle">
            <img :src="require(`../images/icon-${hand}.svg`)" />
          </span>
        </span>
        <h3>YOU PICKED</h3>
      </div>
      <div>
        <span v-if="houseHand.length > 0" :class="`${houseHand}-circle`">
          <span class="circle">
            <img :src="require(`../images/icon-${houseHand}.svg`)" />
          </span>
        </span>
        <span v-else class="empty-circle">
          <span class="circle empty"></span>
        </span>
        <h3>THE HOUSE PICKED</h3>
      </div>
    </div>
    <div v-if="result.length > 0" class="result-container">
      <h1>{{ result }}</h1>
      <a @click="handleGameRestart">PLAY AGAIN</a>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    hand: String
  },
  data() {
    return {
      houseHand: "",
      choices: ["rock", "paper", "scissors"],
      result: ""
    };
  },
  mounted() {
    let val = this.getRandomInt(3);
    setTimeout(() => (this.houseHand = this.choices[val]), 1500);
    setTimeout(() => this.handleResult(), 2000);
  },
  methods: {
    getRandomInt(max) {
      return Math.floor(Math.random() * Math.floor(max));
    },
    handleResult() {
      let userChoice = this.choices.indexOf(this.hand);
      let pcChoice = this.choices.indexOf(this.houseHand);

      userChoice === pcChoice
        ? (this.result = "YOU TIED")
        : pcChoice === this.choices.length - 1 && userChoice === 0
        ? (this.result = "YOU WIN")
        : userChoice === this.choices.length - 1 && pcChoice === 0
        ? (this.result = "YOU LOSE")
        : userChoice > pcChoice
        ? (this.result = "YOU WIN")
        : (this.result = "YOU LOSE");

      this.$emit("result", this.result);
    },
    handleGameRestart() {
      this.houseHand = "";
      this.result = "";
      this.$emit("clicked", true);
    }
  }
};
</script>
