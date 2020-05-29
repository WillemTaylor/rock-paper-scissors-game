<template>
  <div class="header-container">
    <div>
      <h2>
        ROCK
        <br />PAPER
        <br />SCISSORS
      </h2>
    </div>
    <div :class="['scoreboard', showRules ? 'rules' : '']">
      <h5>SCORE</h5>
      <h1>{{ score }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    showRules: Boolean,
    score: Number
  }
};
</script>
