<template>
  <div>
    <h1>TIMER GAME</h1>
    <button @click="start" :disabled="is_playing">Start</button>
    <Block v-if="is_playing" :delay="delay" @endgame="end_game" />
    <Results v-if="score_show" :score="score" />
  </div>
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  data() {
    return {
      is_playing: false,
      delay: null,
      score: null,
      score_show: false,
    };
  },
  components: {
    Block,
    Results,
  },
  methods: {
    start() {
      this.score_show=false;
      this.is_playing = true;
      let ran_time = Math.random() * 5000;
      this.delay = 2000 + ran_time;
    },
    end_game(reactiontime) {
      this.score_show = true;
      this.score = reactiontime;
      this.is_playing = false;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

