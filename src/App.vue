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
      <div class="counter">
        <h1>Score:</h1>
        <h2>{{ score }}</h2>
      </div>
      <div class="counter">
        <h1>High Score:</h1>
        <h2>{{ highScore }}</h2>
      </div>
      <div class="counter">
        <h1>Timer:</h1>
        <h2>{{ timer }}</h2>
      </div>
    </div>
    <Moles v-bind:moleData="moles" v-on:whacked="handleWhacked" />
  </div>
</template>

<script>
import Moles from './components/Moles';

export default {
  name: 'App',
  components: {
    Moles: Moles
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
    handleWhacked: function(idx) {
      console.log('Whacked! App ' + idx);
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
