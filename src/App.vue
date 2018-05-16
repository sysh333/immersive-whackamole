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
    <Moles v-bind:moleData="moles" v-on:whack="handleWhack" />
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
      console.log('I was clicked!');
    },
    handleWhack: function(moleId) {
      this.score++;
    }
  }
}
</script>

<style>
.counter {
  margin: 10px;
  display: inline-block;
}

.mole {
  margin: 10px;
  display: inline-block;
}
</style>
