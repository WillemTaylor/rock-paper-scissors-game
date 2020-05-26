<template>
  <div class="header-container">
    <div>
      <h2>
        ROCK
        <br />PAPER
        <br />SCISSORS
      </h2>
    </div>
    <div class="scoreboard">
      <h5>SCORE</h5>
      <h1>{{ score }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      score: 12
    };
  }
};
</script>
