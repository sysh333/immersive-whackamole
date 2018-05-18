<template>
  <div class="whackamole">
    <h1 class="logo">
      Whackamole
    </h1>
    <button
      class="start-game"
      v-on:click="gameStart"
    >
      Start Game
    </button>
    <div class="counters-container">
      <Counter
        label="Score:"
        v-bind:value="score"
      />
      <Counter
        label="High Score:"
        v-bind:value="highScore"
      />
      <Counter
        label="Timer"
        v-bind:value="timer"
      />
    </div>
    <Moles
      v-bind:moleData="moles"
      v-on:whack="handleMoleWhack"
    />
  </div>
</template>

<script>
import Moles from './components/Moles';
import Counter from './components/Counter';

export default {
  name: 'App',
  components: {
    Moles: Moles,
    Counter: Counter
  },
  data: () => {
    return {
      score: 0,
      highScore: 10,
      timer: 20,
      moles: [false, false, false, false]
    };
  },
  methods: {
    gameStart: function() {
      this.startTimer();
    },
    handleMoleWhack: function(moleId) {
      this.score++;
    },
    startTimer: function() {
      this.timerId = setInterval(() => {
        this.decrementTime();
      }, 1000);
    },
    decrementTime: function() {
      this.timer--;
      if (this.timer === 0) {
        this.stopTimer();
      }
    },
    stopTimer: function() {
      clearInterval(this.timerId);
    }
  }
}
</script>

<style>
.whackamole {
  font-family: Bungee,cursive;
  max-width: 800px;
  width: 100%;
  margin: auto;
  margin-top: 20px;
}
.logo {
  text-align: center;
  margin: 30px;
}
.start-game {
    margin: auto;
    display: block;
}
button {
  font-family: Bungee,cursive;
  padding: 20px;
  border-radius: 3px;
  border: 0;
  background-color: #52b1d6;
  color: #fff;
  font-size: 1em;
  cursor: pointer;
  transition: background-color .2s ease;
}
.counters-container {
  display: flex;
  justify-content: space-around;
  margin-bottom: 20px;
}
</style>
