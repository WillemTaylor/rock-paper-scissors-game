<template>
  <div class="hand-container">
    <div>
      <span
        :class="
          hand === 'paper'
            ? 'paper-circle'
            : hand === 'scissors'
            ? 'scissors-circle'
            : 'rock-circle'
        "
      >
        <span class="circle">
          <img :src="require(`../images/icon-${hand}.svg`)" />
        </span>
      </span>
      <h3>YOU PICKED</h3>
    </div>
    <div v-if="houseHand.length > 0">
      <span
        :class="
          houseHand === 'paper'
            ? 'paper-circle'
            : houseHand === 'scissors'
            ? 'scissors-circle'
            : 'rock-circle'
        "
      >
        <span class="circle">
          <img :src="require(`../images/icon-${houseHand}.svg`)" />
        </span>
      </span>
      <h3>THE HOUSE PICKED</h3>
    </div>
    <div v-else>
      <span class="empty-circle">
        <span class="circle empty"></span>
      </span>
      <h3>THE HOUSE PICKED</h3>
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
      choices: ["paper", "scissors", "rock"]
    };
  },
  mounted() {
    let val = this.getRandomInt(3);
    setTimeout(() => (this.houseHand = this.choices[val]), 1000);
  },
  methods: {
    getRandomInt(max) {
      return Math.floor(Math.random() * Math.floor(max));
    }
  }
};
</script>
