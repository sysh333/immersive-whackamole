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
      v-bind:gameActive="gameActive"
      v-on:whack="handleMoleWhack"
    />
  </div>
</template>

<script>
import Moles from './components/Moles';
import Counter from './components/Counter';

const storageKey = 'whackamole.highscore';
const moleTimers = [0, 0, 0, 0];

export default {
  name: 'App',
  components: {
    Moles: Moles,
    Counter: Counter
  },
  data: () => {
    return {
      score: 0,
      highScore: 0,
      timer: 20,
      moles: [false, false, false, false],
      gameActive: false
    };
  },
  mounted: function () {
    this.$nextTick(function () {
      // ローカルストレージから読み出す
      const savedValue = localStorage.getItem(storageKey);
      if (!isNaN(parseInt(savedValue))) {
        this.highScore = savedValue;
      }
    })
  },
  methods: {
    gameStart: function() {
      // extra1: 何回も"START GAME"できてしまうバグを直す！
      if (this.gameActive) return;
      this.startTimer();
      this.score = 0;
      this.timer = 20;
      this.moles = [false, false, false, false];
      this.gameActive = true;
      this.startMoles();
    },
    endGame: function() {
      this.gameActive = false;
      this.stopTimer();
      this.updateHighScore();
      this.stopMoles();
    },
    updateHighScore: function() {
      this.highScore = Math.max(this.highScore, this.score);
      localStorage.setItem(storageKey, this.highScore);
    },
    handleMoleWhack: function(moleId) {
      if (!this.gameActive) return;
      clearTimeout(moleTimers[moleId]);
      this.deactivateMole(moleId, false);
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
        this.endGame();
      }
    },
    stopTimer: function() {
      clearInterval(this.timerId);
    },
    startMoles: function() {
      this.molesTimer = setInterval(this.activateMoleRandomly.bind(this), 500);
    },
    stopMoles: function() {
      clearInterval(this.molesTimer);
    },
    activateMoleRandomly: function() {
      const index = Math.floor(Math.random() * this.moles.length);
      if (!this.moles[index]) {
        this.activateMole(index);
      }
    },
    activateMole: function(id) {
      // 実際にmolesに情報を更新する
      this.updateMole(id, true);
      moleTimers[id] = setTimeout(this.deactivateMole.bind(this, id), 2500);
    },
    deactivateMole: function(id) {
      // molesに対して情報を更新する
      this.updateMole(id, false);
    },
    updateMole: function(id, active) {
      const moles = this.moles.slice(0);
      moles[id] = active;
      this.moles = moles;
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
