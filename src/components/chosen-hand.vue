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
      <a @click="handleGameReset">PLAY AGAIN</a>
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
      choices: ["paper", "scissors", "rock"],
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
      if (this.hand === "paper") {
        if (this.houseHand === "paper") {
          this.result = "YOU TIED";
        } else if (this.houseHand === "scissors") {
          this.result = "YOU LOSE";
        } else if (this.houseHand === "rock") {
          this.result = "YOU WIN";
        }
      } else if (this.hand === "scissors") {
        if (this.houseHand === "paper") {
          this.result = "YOU WIN";
        } else if (this.houseHand === "scissors") {
          this.result = "YOU TIED";
        } else if (this.houseHand === "rock") {
          this.result = "YOU LOSE";
        }
      } else if (this.hand === "rock") {
        if (this.houseHand === "paper") {
          this.result = "YOU LOSE";
        } else if (this.houseHand === "scissors") {
          this.result = "YOU WIN";
        } else if (this.houseHand === "rock") {
          this.result = "YOU TIED";
        }
      }
      this.$emit("result", this.result);
    },
    handleGameReset() {
      this.houseHand = "";
      this.result = "";
      this.$emit("clicked", true);
    }
  }
};
</script>
